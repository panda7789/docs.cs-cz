---
title: Přidání prvků, atributů a uzlů do stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169572"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>Přidání prvků, atributů a uzlů do stromu XML (C#)
Do existujícího stromu XML můžete přidat obsah (prvky, atributy, komentáře, pokyny pro zpracování, text a CDATA).  
  
## <a name="methods-for-adding-content"></a>Metody přidávání obsahu  
 Následující metody přidávají podřízený obsah do aplikace <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá obsah na konci podřízeného <xref:System.Xml.Linq.XContainer>obsahu .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízeného obsahu . <xref:System.Xml.Linq.XContainer>|  
  
 Následující metody přidávají obsah jako <xref:System.Xml.Linq.XNode>uzly na stejné úrovni . Nejběžnější uzel, do kterého přidáte obsah <xref:System.Xml.Linq.XElement>na stejné úrovni, je , i když <xref:System.Xml.Linq.XText> můžete <xref:System.Xml.Linq.XComment>přidat platný obsah na stejné úrovni do jiných typů uzlů, jako jsou nebo .  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah <xref:System.Xml.Linq.XNode>za .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah <xref:System.Xml.Linq.XNode>před .|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří dva stromy XML a potom upraví jeden ze stromů.  
  
### <a name="code"></a>kód  
  
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
  