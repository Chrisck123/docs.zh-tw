---
title: "疑難排解安裝問題 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 疑難排解安裝問題
本主題會說明如何疑難排解 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 安裝問題。  
  
## 有些 Windows Communication Foundation 登錄機碼 \(Registry Key\) 無法藉由在 .NET Framework 3.0 上執行 MSI 修復作業來加以修復。  
 如果您刪除下列任何登錄機碼：  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelService 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelOperation 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\SMSvcHost 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSDTC Bridge 3.0.0.0  
  
 如果您從 \[**控制台**\] 中的 \[**新增\/移除程式**\] 小程式啟動 .NET Framework 3.0 安裝程式以執行修復，這些機碼仍無法重建。若要正確地重新建立這些機碼，使用者必須解除安裝並重新安裝 .NET Framework 3.0。  
  
## WMI 服務損毀在 .NET Framework 3.0 套件安裝期間封鎖 Windows Communication Foundation WMI 提供者的安裝  
 WMI 服務損毀可能會封鎖 Windows Communication Foundation WMI 提供者的安裝。在進行安裝時，Windows Communication Foundation 安裝程式無法使用 mofcomp.exe 元件來註冊 WCF .mof 檔。可能徵兆如下所示：  
  
1.  .NET Framework 3.0 安裝成功完成，不過 WCF WMI 提供者並未註冊。  
  
2.  應用程式記錄檔中顯示關於在註冊 WCF 的 WMI 提供者、或執行 mofcomp.exe 時所發生問題的錯誤事件。  
  
3.  在使用者的 %temp% 目錄中名為 dd\_wcf\_retCA\* 的安裝記錄檔，包含了無法註冊 WCF WMI 提供者的相關資訊。  
  
4.  在事件記錄檔或安裝追蹤記錄檔中，可能會列出下列其中一個例外狀況 \(Exception\)：  
  
     ServiceModelReg \[11:09:59:046\]: System.ApplicationException: 以 "E:\\WINDOWS\\Microsoft.NET\\Framework\\v3.0\\Windows Communication Foundation\\ServiceModel.mof" 執行 E:\\WINDOWS\\system32\\wbem\\mofcomp.exe 時產生未預期的結果 3  
  
     或：  
  
     ServiceModelReg \[07:19:33:843\]: System.TypeInitializationException: 'System.Management.ManagementPath' 的型別初始設定式發生例外狀況。\-\-\-\> System.Runtime.InteropServices.COMException \(0x80040154\)：由於發生下列錯誤，為具有 CLSID {CF4CC405\-E2C5\-4DDD\-B3CE\-5E7582D8C9FA} 的元件擷取 COM 類別處理站時失敗：80040154。  
  
     或：  
  
     ServiceModelReg \[07:19:32:750\]: System.IO.FileNotFoundException: 無法載入檔案或組件 'C:\\WINDOWS\\system32\\wbem\\mofcomp.exe' 或其相依性的其中之一。系統找不到指定的檔案。  
  
     檔案名稱：'C:\\WINDOWS\\system32\\wbem\\mofcomp.exe  
  
 您必須遵循下列步驟才能解決上述問題。  
  
1.  執行 [WMI 診斷公用程式 2.0版](http://go.microsoft.com/fwlink/?LinkId=94685)以修復 WMI 服務。[!INCLUDE[crabout](../../../includes/crabout-md.md)]使用這項工具的詳細資訊，請參閱 [WMI 診斷公用程式](http://go.microsoft.com/fwlink/?LinkId=94686)主題。  
  
 使用位於 \[**控制台**\] 中的 \[**新增\/移除程式**\] 小程式來修復 .NET Framework 3.0 安裝，或是解除安裝\/重新安裝 .NET Framework 3.0。  
  
## 在安裝 .NET Framework 3.5 後修復 .NET Framework 3.0 會將 machine.config 中由 .NET Framework 3.5 引入的組態項目移除  
 如果您要在安裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 後修復 .NET Framework 3.0，則會將 machine.config 中由 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 引入的組態項目移除。不過，web.config 會保持不變。解決方法是先透過 ARP 移除，再修復 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]，或使用 [WorkFlow 服務登錄工具 \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) 配合 `/c` 參數。  
  
 [WorkFlow 服務登錄工具 \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) 可以在 %windir%\\Microsoft.NET\\framework\\v3.5\\ 或 %windir%\\Microsoft.NET\\framework64\\v3.5\\ 中找到。  
  
## 在安裝 .NET Framework 3.5 之後，適當地為 WCF\/WF Webhost 設定 IIS  
 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 安裝無法設定額外的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \- 相關的 IIS 組態設定時，它會將錯誤記錄在安裝記錄檔中，然後繼續。任何執行 WorkflowServices 應用程式的嘗試都將失敗，因為缺少必要的組態設定。例如，無法載入 xoml 或規則服務。  
  
 若要解決這個問題，請將 [WorkFlow 服務登錄工具 \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) 搭配 `/c` 參數使用，以適當設定電腦上的 IIS 指令碼對應。[WorkFlow 服務登錄工具 \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) 可以在 %windir%\\Microsoft.NET\\framework\\v3.5\\ 或 %windir%\\Microsoft.NET\\framework64\\v3.5\\ 中找到。  
  
## 無法從組件 ‘System.ServiceModel, Version 3.0.0.0, Culture\=neutral, PublicKeyToken\=b77a5c561934e089’ 載入類型 ‘System.ServiceModel.Activation.HttpModule’  
 如果在安裝 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 後啟用 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] HTTP 啟動，則會發生這個錯誤。若要解決這個問題，請從 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 命令提示字元內部執行下列命令列：  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## 請參閱  
 [安裝指示](../../../docs/framework/wcf/samples/set-up-instructions.md)