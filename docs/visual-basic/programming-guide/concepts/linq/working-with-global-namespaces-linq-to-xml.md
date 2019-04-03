---
title: Práce s globálními názvovými prostory (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827377"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Práce s globálními názvovými prostory (Visual Basic) (LINQ to XML)
Jednou z klíčových funkcí literálů XML v jazyce Visual Basic je možnost deklarovat obory názvů XML pomocí `Imports` příkazu. Díky této funkci lze deklarovat obor názvů XML, který používá předponu nebo je možné deklarovat výchozí názvový prostor XML.  
  
 Tato možnost je užitečná ve dvou situacích. Nejprve obory názvů deklarovaný v literálech XML se nepřenesou do vložené výrazy. Deklarace oborů názvů globální snižuje množství práce, které budete muset udělat, abyste použijte vložené výrazy s obory názvů. Za druhé je třeba deklarovat globálními názvovými prostory k použití oborů názvů pomocí vlastnosti XML.  
  
 Je možné deklarovat globální obory názvů na úrovni projektu. Můžete také deklarovat globální obory názvů na úrovni modulu, který přepíše globálními názvovými prostory na úrovni projektu. Nakonec můžete přepsat globální obory názvů v literálu XML.  
  
 Při použití literály XML a vlastnosti XML, které jsou v oborech názvů globálně deklarované, zobrazí se rozbalený název vlastnosti nebo literály XML podržením ukazatele nad nich v sadě Visual Studio. Rozbalený název v popisku se zobrazí.  
  
 Můžete získat <xref:System.Xml.Linq.XNamespace> objekt, který odpovídá globálního oboru názvů pomocí `GetXmlNamespace` metody.  
  
## <a name="examples-of-global-namespaces"></a>Příklady globálními názvovými prostory  
 Následující příklad deklaruje s použitím výchozí globální obor názvů `Imports` příkazu a použití literálu XML k inicializaci <xref:System.Xml.Linq.XElement> objekt v tomto oboru názvů:  
  
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
  
 Následující příklad deklaruje globální obor názvů s předponou a potom použije literál XML elementu inicializace:  
  
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
 Obory názvů, které jsou deklarovány v literálech XML není přenesou do vložené výrazy. Následující příklad deklaruje výchozí obor názvů. Poté použije pro vložený výraz `Child` elementu.  
  
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
  
 Jak je vidět, výsledný XML obsahuje deklaraci výchozí obor názvů tak, aby `Child` elementu je bez oboru názvů.  
  
 Obor názvů v vložený výraz může znovu deklarovat následujícím způsobem:  
  
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
  
 Je to ale těžkopádnější použití než globální výchozí obor názvů, který není lepším řešením. Globální výchozí obor názvů můžete pomocí literálů XML bez deklarace oborů názvů. Výsledného kódu XML se bude v globálně deklarované výchozí obor názvů.  
  
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
  
## <a name="using-namespaces-with-xml-properties"></a>Použití oboru názvů s vlastností XML  
 Pokud pracujete s stromu XML, který je v oboru názvů, a použití vlastností XML, pak musíte použít globální obor názvů tak, aby vlastností XML bude mít i správný obor názvů. Následující příklad deklaruje stromu XML v oboru názvů. Potom zobrazí počet `Child` elementy.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 V tomto příkladu znamená, že neexistují žádné `Child` elementy. Vytvoří následující výstup:  
  
```  
0  
```  
  
 Pokud však deklarovat výchozí globální obor názvů, pak literál XML a vlastnosti XML jsou ve výchozím globálním oboru názvů:  
  
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
  
 V tomto příkladu znamená, že existuje jedna `Child` elementu. Vytvoří následující výstup:  
  
```  
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
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace a globálními názvovými prostory  
 Můžete získat <xref:System.Xml.Linq.XNamespace> s použitím `GetXmlNamespace` metody:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Práce s názvovými prostory XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
