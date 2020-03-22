---
title: Úvod k literálům XML v jazyce Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266947"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Úvod k literálům XML v jazyce Visual Basic
Tato část obsahuje informace o vytváření stromů XML v jazyce Visual Basic.  
  
 Informace o použití výsledků dotazů LINQ jako obsahu pro strom XML naleznete v tématu [Funkční konstrukce (LINQ na XML) (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)  
  
 Další informace o literálech XML v jazyce Visual Basic naleznete v [tématu Přehled LINQ na XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 Následující příklad <xref:System.Xml.Linq.XElement>ukazuje, jak vytvořit , `contacts`v tomto případě :  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Vytvoření prvku XElement s jednoduchým obsahem  
 Můžete vytvořit, <xref:System.Xml.Linq.XElement> který obsahuje jednoduchý obsah, takto:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Můžete vytvořit prázdný <xref:System.Xml.Linq.XElement>, takto:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Použití vložených výrazů  
 Důležitou vlastností literálů XML je, že umožňují vložené výrazy. Vložené výrazy umožňují vyhodnotit výraz a vložit výsledky výrazu do stromu XML. Pokud výraz vyhodnotí typ <xref:System.Xml.Linq.XElement>, prvek je vložen do stromu. Pokud výraz vyhodnotí typ <xref:System.Xml.Linq.XAttribute>, atribut je vložen do stromu. Prvky a atributy můžete vložit do stromu pouze tam, kde jsou platné.  
  
 Je důležité si uvědomit, že pouze jeden výraz může přejít do vloženého výrazu. Nelze vložit více příkazů. Pokud výraz přesahuje jeden řádek, musíte použít znak pokračování řádku.  
  
 Pokud použijete vložený výraz k přidání existujících uzlů (včetně prvků) a atributů do nového stromu XML a pokud jsou existující uzly již nadřazené, uzly jsou klonovány. Nově klonované uzly jsou připojeny k nové stromu XML. Pokud existující uzly nejsou nadřazené, uzly jsou jednoduše připojeny k novému stromu XML. Poslední příklad v tomto tématu ukazuje toto.  
  
 Následující příklad používá vložený výraz k vložení prvku do stromu:  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>Použití vložených výrazů pro obsah  
 Vložený výraz můžete použít k dodání obsahu prvku:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Použití dotazu LINQ ve vloženém výrazu  
 Výsledky dotazu LINQ můžete použít pro obsah prvku:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Použití vložených výrazů pro názvy uzlů  
 Vložené výrazy můžete také použít k výpočtu názvů atributů, hodnot atributů, názvů prvků a hodnot elementů:  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Klonování vs. připojení  
 Jak již bylo zmíněno dříve, pokud použijete vložený výraz k přidání existujících uzlů (včetně prvků) a atributů do nového stromu XML, pokud jsou existující uzly již nadřazené, uzly jsou klonovány a nově klonované uzly jsou připojeny k nové stromu XML. Pokud existující uzly nejsou nadřazené, jsou jednoduše připojeny k nové stromu XML.  
  
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
  
 Tento příklad vytváří následující výstup:  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Viz také

- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
