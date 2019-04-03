---
title: Úvod k Literálům XML v Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841278"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Úvod k Literálům XML v jazyce Visual Basic
Tato část obsahuje informace o vytváření stromů XML v jazyce Visual Basic.  
  
 Informace o použití výsledků dotazů LINQ jako obsah pro stromu XML, naleznete v tématu [funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Další informace o literálech XML v jazyce Visual Basic najdete v tématu [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Vytváření stromů XML  
 Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement>, v tomto případě `contacts`:  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>Vytváření s jednoduchým obsahem na XElement  
 Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah následujícím způsobem:  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Vytvořit prázdný Element  
 Můžete vytvořit prázdnou <xref:System.Xml.Linq.XElement>, následujícím způsobem:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Použitím vložené výrazy  
 Důležité funkce literálů XML je, že umožňují vložené výrazy. Vložené výrazy umožňují vyhodnocení výrazu a vložení výsledků výrazu do stromu XML. Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XElement>, element je vložen do stromu. Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XAttribute>, atribut je vložen do stromu. Elementy a atributy můžete vložit do stromu, pouze pokud jsou platné.  
  
 Je důležité si uvědomit, že pouze jeden výraz můžete přejít do vloženého výrazu. Nelze vložit více příkazů. Pokud výraz se rozpíná za jeden řádek, je nutné použít znak pro pokračování řádku.  
  
 Pokud používáte vložený výraz přidejte existující uzly (včetně prvky) a atributy do nového stromu XML a pokud existující uzly jsou již opatřen podřízeným prvkem, se klonují uzly. Nově naklonované uzly jsou připojené do nového stromu XML. Pokud nejsou nadřazena stávající uzly, uzly připojeny jednoduše do nového stromu XML. V poslední příkladu v tomto tématu ukazuje to.  
  
 Následující příklad používá vložený výraz k vkládání elementů do stromové struktury:  
  
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
  
### <a name="using-embedded-expressions-for-content"></a>Použitím vložené výrazy pro obsah  
 Slouží k poskytování obsahu elementu, můžete použít vložený výraz:  
  
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
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Pomocí dotazu LINQ v vložený výraz  
 Výsledky dotazu LINQ slouží pro obsah elementu:  
  
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
  
### <a name="using-embedded-expressions-for-node-names"></a>Použitím vložené výrazy pro názvy Wwnn  
 Vložené výrazy můžete použít také k výpočtu názvy atributů, hodnoty atributů, názvy prvků a hodnoty prvků:  
  
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
 Jak bylo zmíněno dříve, pokud používáte vložený výraz přidat existující uzly (včetně prvky) a atributy do nového stromu XML, pokud již má nadřazenou existujících uzlů, se klonují uzly a nově naklonované uzly jsou připojené do nového stromu XML. Pokud nejsou nadřazena stávající uzly, jsou jednoduše připojené do nového stromu XML.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
