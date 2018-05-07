---
title: Práce s globální obory názvů (Visual Basic) (technologie LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: c1f34b374f956ec0a8b9658742e529d7ccb1b2ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Práce s globální obory názvů (Visual Basic) (technologie LINQ to XML)
Jedním z klíčových funkcích služby literálů XML v jazyce Visual Basic je schopnost deklarace oborů názvů XML pomocí `Imports` příkaz. Pomocí této funkce lze deklarovat na obor názvů XML, který používá předpony nebo můžou deklarovat výchozí obor názvů XML.  
  
 Tato možnost je užitečná ve dvou situacích. Nejprve obory názvů, které jsou deklarované v literálech XML se nepřenesou do vložené výrazy. Deklarace oborů názvů globální snižuje množství práce, kterou je třeba udělat, aby používat vložené výrazy s obory názvů. Druhý je potřeba deklarovat globální obory názvů chcete-li použít obory názvů XML vlastnostmi.  
  
 Je možné deklarovat globální obory názvů na úrovni projektu. Můžete také deklarovat globální obory názvů na úrovni modulu, která přepisuje obory názvů globální úrovni projektu. Nakonec můžete přepsat globální obory názvů v literál XML.  
  
 Při použití literálů XML nebo XML vlastnosti, které jsou v oborech názvů globálně deklarovat, zobrazí se název rozšířené vlastnosti nebo XML – literály ukázáním v sadě Visual Studio. Zobrazí se název rozšířené ve formě popisu tlačítka.  
  
 Můžete získat <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá globální obor názvů pomocí `GetXmlNamespace` metoda.  
  
## <a name="examples-of-global-namespaces"></a>Příklady globální obory názvů  
 Následující příklad uvádí výchozí globální obor názvů pomocí `Imports` příkaz a pak používá literál XML k chybě při inicializaci <xref:System.Xml.Linq.XElement> objekt v daném oboru názvů:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 Následující příklad prohlašuje globální obor názvů s předponou a pak použije literál XML k chybě při inicializaci elementu.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Globální obory názvů a vložené výrazy  
 Obory názvů, které jsou deklarované v literálech XML se nepřenesou do vložené výrazy. Následující příklad uvádí výchozí obor názvů. Poté použije embedded výrazu pro `Child` elementu.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Jak vidíte, výsledná XML zahrnuje deklaraci výchozí obor názvů tak, aby `Child` elementu je žádný obor názvů.  
  
 Obor názvů embedded výrazu může deklarovat znovu následujícím způsobem:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 To je však těžkopádnější používat než globální výchozí obor názvů, který je lepší přístup. V globální výchozí obor názvů můžete použít literálů XML bez deklarace oborů názvů. Výsledný soubor XML se bude v globálně deklarovaný výchozí obor názvů.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>Obory názvů pomocí vlastnosti XML.  
 Pokud pracujete s XML stromové struktury, která je v oboru názvů, a pomocí vlastnosti XML, pak musíte použít globální obor názvů tak, aby vlastností XML bude taky v správný obor názvů. Následující příklad deklaruje strom XML v oboru názvů. Potom vytiskne počet `Child` elementy.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Tento příklad určuje, že neexistují žádné `Child` elementy. Vytváří následující výstup:  
  
```  
0  
```  
  
 Pokud však deklarovat výchozí globální obor názvů, pak literál XML a vlastnosti XML v jsou výchozí globální obor názvů:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 Tento příklad znamená, že existuje jedna `Child` elementu. Vytváří následující výstup:  
  
```  
1  
```  
  
 Pokud je deklarovat globální obor názvů, který má předponu, můžete použít předponu pro literály XML a vlastnosti XML:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace a globálních oborech názvů  
 Můžete získat <xref:System.Xml.Linq.XNamespace> objekt pomocí `GetXmlNamespace` metoda:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Viz také  
 [Práce s obory názvů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
