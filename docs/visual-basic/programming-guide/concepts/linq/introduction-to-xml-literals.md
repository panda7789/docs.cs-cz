---
title: Úvod do literálů XML v jazyce Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397581"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Úvod do literálů XML v Visual Basic
Tato část poskytuje informace o vytváření stromů XML v Visual Basic.  
  
 Informace o použití výsledků dotazů LINQ jako obsahu stromu XML naleznete v tématu [funkční konstrukce (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).  
  
 Další informace o literálech XML v Visual Basic najdete v tématu [přehled LINQ to XML v Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement> , v tomto případě `contacts` :  
  
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
 Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah, a to následujícím způsobem:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Vytvoření prázdného prvku  
 Prázdné můžete vytvořit takto <xref:System.Xml.Linq.XElement> :  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Použití vložených výrazů  
 Důležitou funkcí literálů XML je, že umožňují vložené výrazy. Vložené výrazy umožňují vyhodnotit výraz a vložit výsledky výrazu do stromu XML. Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XElement> , je prvek vložen do stromu. Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XAttribute> , je do stromu vložen atribut. Prvky a atributy lze vložit do stromu pouze v případě, že jsou platné.  
  
 Je důležité si uvědomit, že do vloženého výrazu může přejít pouze jeden výraz. Nelze vložit více příkazů. Pokud výraz překračuje jeden řádek, je nutné použít znak pro pokračování řádku.  
  
 Použijete-li vložený výraz pro přidání existujících uzlů (včetně prvků) a atributů do nového stromu XML a pokud již existující uzly jsou nadřazené, uzly budou klonovány. Nově klonované uzly jsou připojeny k novému stromu XML. Pokud existující uzly nejsou nadřazené, uzly jsou jednoduše připojeny k novému stromu XML. Příklad ukazuje poslední příklad v tomto tématu.  
  
 Následující příklad používá vložený výraz pro vložení elementu do stromu:  
  
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
  
### <a name="using-embedded-expressions-for-content"></a>Použití vložených výrazů pro obsah  
 Můžete použít vložený výraz k poskytnutí obsahu prvku:  
  
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
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Použití dotazu LINQ ve vloženém výrazu  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Použití vložených výrazů pro názvy uzlů  
 Vložené výrazy lze také použít pro výpočet názvů atributů, hodnot atributů, názvů prvků a hodnot elementů:  
  
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
  
### <a name="cloning-vs-attaching"></a>Klonování versus připojení  
 Jak bylo zmíněno dříve, pokud použijete vložený výraz pro přidání existujících uzlů (včetně prvků) a atributů do nového stromu XML, pokud již existující uzly jsou nadřazené, uzly budou klonovány a nově naklonované uzly jsou připojeny k novému stromu XML. Pokud existující uzly nejsou nadřazené, jsou jednoduše připojeny k novému stromu XML.  
  
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
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Viz také

- [Vytváření stromů XML (Visual Basic)](creating-xml-trees.md)
