---
title: Přidání elementů, atributů a uzlů do stromu XML
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 5b80a19c952388c2591536077f382df2f69fe80f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383894"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>Přidání elementů, atributů a uzlů do stromu XML (Visual Basic)
Do existujícího stromu XML můžete přidat obsah (prvky, atributy, komentáře, instrukce pro zpracování, text a CDATA).  
  
## <a name="methods-for-adding-content"></a>Metody pro přidání obsahu  
 Následující metody přidají podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> :  
  
|Metoda|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá obsah na konec podřízeného obsahu <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer> .|  
  
 Následující metody přidávají obsah jako uzly na stejné úrovni <xref:System.Xml.Linq.XNode> . Nejběžnější uzel, do kterého můžete přidat obsah na stejné úrovni <xref:System.Xml.Linq.XElement> , je, i když můžete přidat platný obsah na stejné úrovni k jiným typům uzlů, například <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment> .  
  
|Metoda|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah za <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah před <xref:System.Xml.Linq.XNode> .|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Description  
 Následující příklad vytvoří dvě stromy XML a pak upraví jednu z stromů.  
  
### <a name="code"></a>Kód  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a>Komentáře  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také

- [Úprava stromů XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
