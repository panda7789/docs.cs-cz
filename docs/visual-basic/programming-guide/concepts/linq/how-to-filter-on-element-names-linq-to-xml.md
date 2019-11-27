---
title: 'Postupy: filtrování názvů prvků (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: 0c443ffa17f7bd4f7537068b97165cda97a37ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353023"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a>Postupy: filtrování názvů elementů (LINQ to XML) (Visual Basic)
Při volání jedné z metod, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, můžete filtrovat podle názvu elementu.  
  
## <a name="example"></a>Příklad  
 Tento příklad načte kolekci následníků, které jsou filtrovány tak, aby obsahovaly pouze následníky se zadaným názvem.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 Další metody, které vracejí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Collections, se řídí stejným vzorem. Signatury jsou podobné <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>. Následuje úplný seznam metod, které mají podobné signatury metody:  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Tento kód generuje následující výstup:  
  
```console  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
