---
title: Práce s globálními názvovými prostory (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350999"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Práce s globálním oborem názvů (Visual Basic) (LINQ to XML)
Jedna z klíčových funkcí literálů XML v Visual Basic je schopnost deklarovat obory názvů XML pomocí příkazu `Imports`. Pomocí této funkce můžete deklarovat obor názvů XML, který používá předponu, nebo můžete deklarovat výchozí obor názvů XML.  
  
 Tato funkce je užitečná ve dvou situacích. Nejprve se obory názvů deklarované v literálech XML nepřenášejí do vložených výrazů. Deklarace globálních oborů názvů snižuje množství práce, které je třeba provést, aby bylo možné použít vložené výrazy s obory názvů. Za druhé musíte deklarovat globální obory názvů, aby bylo možné používat obory názvů s vlastnostmi XML.  
  
 Globální obory názvů můžete deklarovat na úrovni projektu. Můžete také deklarovat globální obory názvů na úrovni modulu, který přepíše globální obory názvů na úrovni projektu. Nakonec můžete přepsat globální obory názvů v literálu XML.  
  
 Při použití literálů XML nebo vlastností XML, které jsou v globálně deklarovaných oborech názvů, můžete zobrazit rozbalený název literálů XML nebo vlastností tak, že na ně najedete myší v aplikaci Visual Studio. Rozbalený název se zobrazí v popisu tlačítka.  
  
 Můžete získat objekt <xref:System.Xml.Linq.XNamespace>, který odpovídá globálnímu oboru názvů pomocí metody `GetXmlNamespace`.  
  
## <a name="examples-of-global-namespaces"></a>Příklady globálních oborů názvů  
 Následující příklad deklaruje výchozí globální obor názvů pomocí příkazu `Imports` a poté používá literál XML pro inicializaci objektu <xref:System.Xml.Linq.XElement> v tomto oboru názvů:  
  
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
  
 Následující příklad deklaruje globální obor názvů s předponou a poté používá literál XML pro inicializaci elementu:  
  
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
 Obory názvů, které jsou deklarovány v literálech XML, se nepřenášejí do vložených výrazů. Následující příklad deklaruje výchozí obor názvů. Potom používá vložený výraz pro prvek `Child`.  
  
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
  
 Jak vidíte, výsledný kód XML obsahuje deklaraci výchozího oboru názvů tak, aby `Child` element není v oboru názvů.  
  
 Můžete znovu deklarovat obor názvů ve vloženém výrazu následujícím způsobem:  
  
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
  
 Je to ale více náročný na použití než globální výchozí obor názvů, což je lepší přístup. S globálním výchozím oborem názvů můžete použít literály XML bez deklarování oborů názvů. Výsledný kód XML bude v globálně deklarovaném výchozím oboru názvů.  
  
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
  
## <a name="using-namespaces-with-xml-properties"></a>Používání oborů názvů s vlastnostmi XML  
 Pokud pracujete se stromovou strukturou XML, která je v oboru názvů a používáte vlastnosti XML, je nutné použít globální obor názvů tak, aby vlastnosti XML byly také ve správném oboru názvů. Následující příklad deklaruje strom XML v oboru názvů. Pak vytiskne počet `Child` prvků.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Tento příklad označuje, že nejsou k dispozici žádné prvky `Child`. Generuje následující výstup:  
  
```console  
0  
```  
  
 Pokud však deklarujete výchozí globální obor názvů, pak je literál XML i vlastnost XML ve výchozím globálním oboru názvů:  
  
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
  
 Tento příklad označuje, že existuje jeden `Child` element. Generuje následující výstup:  
  
```console  
1  
```  
  
 Pokud deklarujete globální obor názvů, který má předponu, můžete použít předponu pro literály XML a vlastnosti XML:  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace a globální obory názvů  
 Objekt <xref:System.Xml.Linq.XNamespace> můžete získat pomocí metody `GetXmlNamespace`:  
  
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
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Viz také:

- [Přehled oborů názvů (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
