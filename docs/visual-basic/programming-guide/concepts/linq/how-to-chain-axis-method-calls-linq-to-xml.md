---
title: 'Postupy: tvoří řetěz volání metod osy (technologie LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: b90cd757429639483f11427e2747c7dd3db9e07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643299"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>Postupy: tvoří řetěz volání metod osy (technologie LINQ to XML) (Visual Basic)
Volání metody osy a pak volání některá z rozšíření metoda OS je běžný vzor, který budete používat v kódu.  
  
 Existují dvě osy s názvem `Elements` kolekci elementů, které vracejí: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metoda. Tyto dvě osy najít všechny elementy zadaným názvem v daném hloubce ve stromové struktuře můžete kombinovat.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> a <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> najdete všechny `Name` elementy ve všech `Address` elementy ve všech `PurchaseOrder` elementy.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Toto funguje, protože jeden z implementace `Elements` osy je jako metody rozšíření na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> odvozená z <xref:System.Xml.Linq.XContainer>, takže můžete volat <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodu výsledky volání <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metoda.  
  
## <a name="example"></a>Příklad  
 V některých případech můžete obnovit všechny elementy při hloubce určitý element když existuje může nebo nemusí být použité nadřazených. Například v následujícím dokumentu, můžete chtít načíst všechny `ConfigParameter` prvky, které jsou podřízené objekty `Customer` elementu, ale ne `ConfigParameter` tedy podřízenou `Root` elementu.  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 Chcete-li to provést, můžete použít <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osy, následujícím způsobem:  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejným způsobem pro formát XML, který je v oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML osy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
