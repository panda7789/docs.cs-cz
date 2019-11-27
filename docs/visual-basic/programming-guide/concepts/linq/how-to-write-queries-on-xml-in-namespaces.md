---
title: 'Postupy: zápis dotazů do XML v oborech názvů'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 496cf8daf5136e8aafff000312bbd730a5152e9f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344462"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)
Chcete-li zapsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 V Visual Basic Nejběžnějším přístupem je definování globálního oboru názvů a pak použití literálů XML a vlastností XML, které používají globální obor názvů. Můžete definovat globální výchozí obor názvů. v takovém případě prvky v literálech XML budou ve výchozím nastavení v oboru názvů. Alternativně můžete definovat globální obor názvů s předponou a potom použít předponu podle požadavků v literálech XML a ve vlastnostech XML. Stejně jako u jiných forem XML nejsou atributy ve výchozím nastavení vždy v žádném oboru názvů.  
  
 První sada příkladů v tomto tématu ukazuje, jak vytvořit strom XML ve výchozím oboru názvů. Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří strom XML, který je ve výchozím oboru názvů. Poté načte kolekci prvků.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
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
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
1  
2  
3  
```  
  
## <a name="example"></a>Příklad  
 V Visual Basic však zápis dotazů ve stromu XML, který používá obor názvů s předponou, je poměrně jiný než dotazování stromu XML ve výchozím oboru názvů. Obvykle se používá příkaz `Imports` pro import oboru názvů s předponou. Pak použijte předponu v názvu elementu a atributu při vytváření stromu XML. Také použijte předponu při dotazování stromu XML pomocí vlastností XML.  
  
 Následující příklad vytvoří strom XML, který je v oboru názvů s předponou. Poté načte kolekci prvků.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
