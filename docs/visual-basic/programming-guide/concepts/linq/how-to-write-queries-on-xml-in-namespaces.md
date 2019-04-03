---
title: 'Postupy: Vytváření dotazů na XML v oborech názvů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 4efa1de254a0264752514c5ae6e601a66fa56f95
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833435"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Postupy: Vytváření dotazů na XML v oborech názvů (Visual Basic)
Chcete-li napsat dotaz na XML, který je v oboru názvů, musíte použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 V jazyce Visual Basic je nejběžnější přístup k definování globální obor názvů a pak použijte literály XML a vlastnosti XML, které používají globální obor názvů. Můžete definovat globální výchozí obor názvů, v takovém případě se v oboru názvů ve výchozím nastavení bude prvků v literálech XML. Alternativně můžete definovat globální obor názvů s předponou a pak použijte předponu podle potřeby literály XML a vlastnosti XML. Stejně jako u jiných forem XML atributy se vždycky nacházejí v žádný obor názvů, ve výchozím nastavení.  
  
 První sada příklady v tomto tématu ukazuje, jak vytvořit stromu XML ve výchozím oboru názvů. Druhá sada ukazuje postup vytvoření stromu XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří stromu XML, který je ve výchozím oboru názvů. Potom načte kolekci elementů.  
  
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
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Příklad  
 V jazyce Visual Basic však zápis dotazů ve stromu XML, který používá obor názvů s předponou je značně odlišná z dotazu stromu XML ve výchozím oboru názvů. Obvykle použijete `Imports` smlouvu pro import oboru názvů s předponou. Pak použijete předponu v názvech prvků a atributů při vytváření stromu XML. Použijete také předponu, při dotazování stromu XML pomocí vlastnosti XML.  
  
 Následující příklad vytvoří stromu XML, který je v oboru názvů s předponou. Potom načte kolekci elementů.  
  
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
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Viz také:

- [Práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
