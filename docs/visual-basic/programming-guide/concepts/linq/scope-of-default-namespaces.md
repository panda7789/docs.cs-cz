---
title: Obor výchozích názvových prostorů
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343648"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Rozsah výchozích oborů názvů v Visual Basic
Výchozí obory názvů jako reprezentované ve stromu XML nejsou v oboru pro dotazy. Pokud máte XML, které je ve výchozím oboru názvů, je stále nutné deklarovat <xref:System.Xml.Linq.XNamespace> proměnnou a zkombinovat ji s místním názvem, aby byl v dotazu použit kvalifikovaný název.  
  
 Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud má strom XML výchozí obor názvů, vývojář někdy zapíše dotaz, jako by kód XML nebyl v oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje typický způsob, jakým je načten XML ve výchozím oboru názvů, ale dotaz je nesprávně zadán.  
  
 Druhá sada příkladů ukazuje nezbytné opravy, aby bylo možné dotazovat XML v oboru názvů.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdnou sadu výsledků dotazu.  
  
### <a name="code"></a>Kód  
  
```vb  
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
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výsledek:  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je správně kódován.  
  
 Na rozdíl od nesprávně uvedeného kódovaného příkladu je správný přístup při použití Visual Basic deklarovat a inicializovat globální výchozí obor názvů. Tím se umístí všechny vlastnosti XML ve výchozím oboru názvů. V příkladu nejsou k dispozici žádné další úpravy, aby mohla správně fungovat.  
  
### <a name="code"></a>Kód  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výsledek:  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
