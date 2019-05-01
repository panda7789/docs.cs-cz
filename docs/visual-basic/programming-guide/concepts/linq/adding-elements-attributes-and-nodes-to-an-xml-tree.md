---
title: Přidání elementů, atributů a uzlů do stromu XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 35d3bdb27342dd7a871778ad4749db4d6849bd60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021853"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>Přidání elementů, atributů a uzlů do stromu XML (Visual Basic)
Obsah (elementy, atributy, komentáře, pokyny pro zpracování, text a CDATA) můžete přidat do existující stromu XML.  
  
## <a name="methods-for-adding-content"></a>Metody pro přidávání obsahu  
 Podřízený obsah k přidání následujících metod <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá obsah na konci podřízený obsah <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízený obsah <xref:System.Xml.Linq.XContainer>.|  
  
 Následující metody přidat jako uzly na stejné úrovni obsah <xref:System.Xml.Linq.XNode>. Nejběžnější uzel, do které přidáte na stejné úrovni obsah je <xref:System.Xml.Linq.XElement>, i když přidáte na stejné úrovni platný obsah na jiné typy uzlů, jako <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah před <xref:System.Xml.Linq.XNode>.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří dvě stromů XML a pak jednu z stromy upraví.  
  
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
 Tento kód vytvoří následující výstup:  
  
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
  
## <a name="see-also"></a>Viz také:

- [Změna stromů XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
