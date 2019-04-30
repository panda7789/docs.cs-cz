---
title: 'Postupy: Ladění prázdných sad výsledků dotazu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 80e505be03a26f80bbba9d3673732505b27e9598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855683"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Postupy: Ladění prázdných sad výsledků dotazu (Visual Basic)
Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotaz jakoby nebyly v oboru názvů XML.  
  
 První sada příklady v tomto tématu ukazuje typické tak, že je načteno XML ve výchozím oboru názvů a dotazuje se nesprávně.  
  
 Druhá sada příklady ukazují potřebné opravy tak, aby můžete dát dotaz na XML v oboru názvů.  
  
 Další informace najdete v tématu [práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdný výsledek sadu.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
        <Child>1</Child>  
        <Child>2</Child>  
        <Child>3</Child>  
        <AnotherChild>4</AnotherChild>  
        <AnotherChild>5</AnotherChild>  
        <AnotherChild>6</AnotherChild>  
    </Root>  
Dim c1 As IEnumerable(Of XElement) = _  
        From el In root.<Child> _  
        Select el  
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 Tento příklad vytvoří následující výsledek:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.  
  
 Řešením je deklarovat a inicializovat globální výchozí obor názvů. To umístí všechny vlastnosti XML ve výchozím oboru názvů. Žádné úpravy jsou požadovány v příkladu, aby to fungovalo správně.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výsledek:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Viz také:

- [Základní dotazy (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
