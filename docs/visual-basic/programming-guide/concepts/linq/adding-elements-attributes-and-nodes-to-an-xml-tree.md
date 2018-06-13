---
title: Přidání prvky, atributy a uzly na strom XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 86d28f5974e30a9b7f1a1e830cd40c3cd916e8ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643010"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>Přidání prvky, atributy a uzly na strom XML (Visual Basic)
Obsah (elementy, atributy, komentáře, pokyny pro zpracování, text a CDATA) můžete přidat na stávající strom XML.  
  
## <a name="methods-for-adding-content"></a>Metody pro přidávání obsahu  
 Následující metody přidat podřízené obsah tak, aby <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá obsah na konci obsahu z podřízené <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízené obsah <xref:System.Xml.Linq.XContainer>.|  
  
 Následující metody přidat jako uzly na stejné úrovni jako obsah <xref:System.Xml.Linq.XNode>. Nejběžnější uzel, do níž přidáváte obsah na stejné úrovni jako je <xref:System.Xml.Linq.XElement>, i když na stejné úrovni jako platný obsah na jiné typy uzlů můžete přidat například <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsahu před <xref:System.Xml.Linq.XNode>.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří dvě stromy XML a pak upravením mezi stromy.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Úprava XML stromů (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
