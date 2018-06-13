---
title: 'Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: f4e895e560d0fb11c128248e4f42d1d5124bc124
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645561"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>Postupy: zápis dotazů na XML v oborech názvů (Visual Basic)
Pokud chcete napsat dotaz na XML, který je v oboru názvů, je nutné použít <xref:System.Xml.Linq.XName> objekty, které mají správný obor názvů.  
  
 Nejběžnější přístupem v jazyce Visual Basic je definovat globální obor názvů a pak použijte literály XML a vlastnosti XML, které používají globální obor názvů. Můžete definovat výchozí globální obor názvů, v takovém případě se v oboru názvů ve výchozím nastavení bude elementy v literálech XML. Alternativně můžete definovat globální obor názvů s předponou a pak použijte předponu podle potřeby v literálech XML a vlastnosti XML. Stejně jako u jiných forem XML atributy se vždycky nacházejí v žádný obor názvů ve výchozím nastavení.  
  
 První sadu příklady v tomto tématu ukazuje, jak vytvořit strom XML ve výchozí obor názvů. Druhá sada ukazuje, jak vytvořit strom XML v oboru názvů s předponou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří ve stromu XML, který je ve výchozí obor názvů. Potom načte kolekci elementů.  
  
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
 V jazyce Visual Basic ale zápis dotazů ve stromové struktuře XML, který používá obor názvů s předponou se poměrně liší od dotazování strom XML v výchozí obor názvů. Obvykle použijete `Imports` příkaz pro import oboru názvů s předponou. Pak použijete předponu v názvech elementu a atributu při vytvoření stromové struktuře XML. Můžete také používat předponu při dotazování strom XML pomocí vlastností XML.  
  
 Následující příklad vytvoří strom XML, který je v oboru názvů s předponou. Potom načte kolekci elementů.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
