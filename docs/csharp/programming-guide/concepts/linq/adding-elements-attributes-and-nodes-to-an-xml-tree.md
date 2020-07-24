---
title: Přidání elementů, atributů a uzlů do stromu XML (C#)
description: Další informace o metodách přidání obsahu, například prvků, atributů, komentářů, instrukcí pro zpracování a textu do existujícího stromu XML.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105554"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>Přidání elementů, atributů a uzlů do stromu XML (C#)
Do existujícího stromu XML můžete přidat obsah (prvky, atributy, komentáře, instrukce pro zpracování, text a CDATA).  
  
## <a name="methods-for-adding-content"></a>Metody pro přidání obsahu  
 Následující metody přidají podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> :  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá obsah na konec podřízeného obsahu <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer> .|  
  
 Následující metody přidávají obsah jako uzly na stejné úrovni <xref:System.Xml.Linq.XNode> . Nejběžnější uzel, do kterého můžete přidat obsah na stejné úrovni <xref:System.Xml.Linq.XElement> , je, i když můžete přidat platný obsah na stejné úrovni k jiným typům uzlů, například <xref:System.Xml.Linq.XText> nebo <xref:System.Xml.Linq.XComment> .  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah za <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah před <xref:System.Xml.Linq.XNode> .|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří dvě stromy XML a pak upraví jednu z stromů.  
  
### <a name="code"></a>Kód  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
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
  