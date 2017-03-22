---
title: "LINQ to XML 軸心方法 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4d6466a78c3a8e9d21e30f2d3cf8a49ed89dafbf
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML 軸心方法 (Visual Basic)
建立 XML 樹狀結構，或將 XML 文件載入到 XML 樹狀結構後，您可以進行查詢以尋找項目和屬性並擷取其值。  
  
 在撰寫任何查詢之前，您必須了解 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 座標軸。 有兩種類型的座標軸方法︰ 首先，有的方法，讓您在單一呼叫<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件，或<xref:System.Xml.Linq.XNode>物件。</xref:System.Xml.Linq.XNode> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 這些方法在單一物件上運作，並傳回的集合<xref:System.Xml.Linq.XElement>， <xref:System.Xml.Linq.XAttribute>，或<xref:System.Xml.Linq.XNode>物件。</xref:System.Xml.Linq.XNode> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 第二，在集合上有可運算的擴充方法，並傳回集合。 擴充方法會列舉來源集合、在集合的每個項目上呼叫適當的座標軸方法，然後串連結果。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[LINQ to XML 軸心方法概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|定義座標軸並說明如何在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢的內容中使用這些座標軸。|  
|[如何︰ 擷取項目 (LINQ to XML) 的集合 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|介紹<xref:System.Xml.Linq.XContainer.Elements%2A>方法。</xref:System.Xml.Linq.XContainer.Elements%2A> 此方法會擷取項目之子項目的集合。|  
|[如何︰ 擷取項目 (LINQ to XML) 的值 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|示範如何取得項目的值。|  
|[如何︰ 篩選項目名稱 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|顯示使用座標軸時，如何在項目名稱上篩選。|  
|[如何︰ 鏈結軸心方法呼叫 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|示範如何將呼叫鏈結到座標軸方法。|  
|[如何︰ 擷取單一子項目 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|顯示如何擷取項目的單一子項目 (假設有子項目的標記名稱)。|  
|[如何︰ 擷取屬性 (LINQ to XML) 的集合 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|介紹<xref:System.Xml.Linq.XElement.Attributes%2A>方法。</xref:System.Xml.Linq.XElement.Attributes%2A> 這個方法會擷取項目的屬性。|  
|[如何︰ 擷取單一屬性 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|顯示如何擷取項目的單一屬性 (假設有屬性名稱)。|  
|[如何︰ 擷取屬性 (LINQ to XML) 的值 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|示範如何取得屬性的值。|  
|[如何︰ 擷取表層值的項目 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|示範如何擷取項目的表層值。|  
|[Visual Basic (LINQ to XML) 中的 已整合語言的軸心方法](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|摘要說明[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]整合軸。|  
  
## <a name="see-also"></a>另請參閱  
 [程式設計手冊 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)