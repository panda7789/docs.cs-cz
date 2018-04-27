---
title: Úvod do literálů XML v Visual Basic2
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 112c1d898c3cdf14b52d843dee8f5a51002be858
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Úvod do literálů XML v jazyce Visual Basic
Tato část obsahuje informace o vytváření stromů XML v jazyce Visual Basic.  
  
 Informace o použití výsledky dotazů LINQ jako obsah pro strom XML najdete v tématu [funkční konstrukce (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Další informace o literálech XML v jazyce Visual Basic, najdete v části [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement>, v takovém případě `contacts`:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>Vytvoření XElement s jednoduchým obsahem  
 Můžete vytvořit <xref:System.Xml.Linq.XElement> obsahující jednoduchým obsahem, následujícím způsobem:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Můžete vytvořit prázdnou <xref:System.Xml.Linq.XElement>, a to takto:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Pomocí vložené výrazy  
 Důležitou součást literálů XML je, že umožňují vložené výrazy. Vložené výrazy umožňují vyhodnocení výrazu a vložit výsledky výraz do stromu XML. Pokud je výsledkem typu <xref:System.Xml.Linq.XElement>, element budou vložena do stromu. Pokud je výsledkem typu <xref:System.Xml.Linq.XAttribute>, atribut se vloží do stromu. Elementy a atributy můžete vložit do stromu jenom tam, kde jsou platné.  
  
 Je důležité si uvědomit, že pouze jeden výraz můžete přejít do embedded výrazu. Nelze vložit více příkazů. Pokud výraz přesahuje jeden řádek, je nutné použít znak pokračování řádku.  
  
 Používáte-li přidat existující uzly (včetně elementů) a atributy, které mají novou větev XML a pokud jsou na uzlech existujícího již nadřazena embedded výrazu, můžete se klonují uzly. Nově naklonovaný uzly jsou připojené k nové stromu XML. Pokud nejsou na uzlech existujícího nadřazena, uzly jsou jednoduše připojit ke stromu nové XML. Poslední příklad v tomto tématu ukazuje to.  
  
 Následující příklad používá výraz embedded vložení prvku do stromu:  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>Pomocí vložené výrazy pro obsah  
 Výraz embedded můžete použít k poskytování obsahu elementu:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Použití v Embedded výrazu dotazu LINQ  
 Výsledky dotazu LINQ můžete použít pro obsah elementu:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Použití vložené výrazy pro názvy  
 Vložené výrazy můžete také použít k výpočtu názvy atributů, hodnoty atributu, elementu názvy a hodnoty element:  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Klonování vs. Připojení  
 Jak je uvedeno výše, pokud používáte embedded výrazu přidejte existující uzly (včetně elementů) a atributy novou větev XML, pokud jsou na uzlech existujícího již nadřazena, uzly jsou klonovat a nově naklonovaný uzly jsou připojené k nové stromu XML. Pokud nejsou na uzlech existujícího nadřazena, jsou jednoduše připojené k nové stromu XML.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
