---
title: 'Postupy: ladění sady výsledků dotazu prázdný (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 33dcfe9b0c0ad41353ca845ed4d8e21ff77292df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>Postupy: ladění sady výsledků dotazu prázdný (Visual Basic)
Jeden z nejběžnějších problémů při dotazování stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotazu, jako by soubor XML není v oboru názvů.  
  
 První sadu příklady v tomto tématu ukazuje obvyklým způsobem, že je načteno kód XML v výchozí obor názvů a je dotazován nesprávně.  
  
 Druhá sada příklady zobrazit potřebné opravy tak, aby v oboru názvů se můžete dotazovat XML.  
  
 Další informace najdete v tématu [práci s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a nastavte dotaz, který vrací prázdný výsledek.  
  
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
  
 Řešení je deklarace a inicializace globální výchozí obor názvů. Tato výchozí obor názvů umístí všechny vlastnosti XML. Žádné další úpravy jsou požadovány v příkladu, aby byla správně fungovat.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Základní dotazy (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
