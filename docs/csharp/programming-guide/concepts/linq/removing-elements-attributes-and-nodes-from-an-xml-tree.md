---
title: Odebrání prvků, atributů a uzlů ze stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591256"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Odebrání prvků, atributů a uzlů ze stromu XML (C#)

Můžete upravit strom XML, odebrat prvky, atributy a další typy uzlů.

Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché. Však při odebírání kolekce prvků nebo atributů, měli byste nejprve zhmotnit kolekci do seznamu a potom odstranit prvky nebo atributy ze seznamu. Nejlepším přístupem je použití <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření, která to udělá za vás.

Hlavním důvodem je, že většina kolekcí, které načtete ze stromu XML, jsou výsledkem pomocí odloženého spuštění. Pokud je nejprve nezhmotníte do seznamu nebo pokud nepoužíváte metody rozšíření, je možné se setkat s určitou třídou chyb. Další informace naleznete [v tématu Smíšené deklarativní kód/imperativní kód chyby (LINQ do XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Následující metody odeberou uzly a atributy ze stromu XML.

|Metoda|Popis|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XAttribute> a z jeho nadřazené.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer>.|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odebere obsah a atributy z . <xref:System.Xml.Linq.XElement>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy . <xref:System.Xml.Linq.XElement>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, odebere atribut.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, odebere podřízený prvek.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XNode> a z jeho nadřazené.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Odebere každý atribut nebo prvek ve zdrojové kolekci z nadřazeného prvku.|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tento příklad ukazuje tři přístupy k odebrání prvků. Nejprve odebere jeden prvek. Za druhé načte kolekci prvků, materializes <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> je pomocí operátoru a odebere kolekci. Nakonec načte kolekci prvků a odebere <xref:System.Xml.Linq.Extensions.Remove%2A> je pomocí metody rozšíření.

Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru naleznete v [tématu Převod datových typů (C#)](./converting-data-types.md).

### <a name="code"></a>kód

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a>Komentáře

Výsledkem tohoto kódu je následující výstup:

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

Všimněte si, že první prvek `Child1`vnouče byl odebrán z . Všechny prvky vnoučat byly `Child2` odebrány z a z `Child3`.
