---
title: Dotazování na XDocument vs. dotazování na XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396295"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>Dotazování na XDocument a dotazování na XElement (Visual Basic)
Když načtete dokument prostřednictvím <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , všimnete si, že budete muset psát dotazy trochu jinak než při načítání prostřednictvím <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>Porovnání XDocument. Load a XElement. Load  
 Když načtete dokument XML do <xref:System.Xml.Linq.XElement> Via, v <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement> kořenu stromu XML obsahuje kořenový prvek načteného dokumentu. Nicméně když načtete stejný dokument XML do <xref:System.Xml.Linq.XDocument> Via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> , kořen stromové struktury je <xref:System.Xml.Linq.XDocument> uzel a kořenový prvek načteného dokumentu je jeden povolený podřízený <xref:System.Xml.Linq.XElement> uzel <xref:System.Xml.Linq.XDocument> . [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Osy pracují relativně ke kořenovému uzlu.  
  
 Tento první příklad načte strom XML pomocí <xref:System.Xml.Linq.XElement.Load%2A> . Pak se dotazuje na podřízené prvky kořenového adresáře stromu.  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Jak je očekáváno, tento příklad vytvoří následující výstup:  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 Následující příklad je stejný jako ten výše, s výjimkou, že je strom XML načten do <xref:System.Xml.Linq.XDocument> namísto <xref:System.Xml.Linq.XElement> .  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 Všimněte si, že stejný dotaz vrátil jeden `Root` uzel místo tří podřízených uzlů.  
  
 Jedním z přístupů k tomu, abyste se s ním mohli pracovat, je použít <xref:System.Xml.Linq.XDocument.Root%2A> vlastnost před přístupem k metodám OS následujícím způsobem:  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 Tento dotaz teď funguje stejným způsobem jako dotaz na stromové struktuře, ve které se nachází root <xref:System.Xml.Linq.XElement> . Tento příklad vytvoří následující výstup:  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>Viz také

- [Základní dotazy (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
