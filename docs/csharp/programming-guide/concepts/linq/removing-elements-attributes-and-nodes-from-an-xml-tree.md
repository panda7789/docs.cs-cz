---
title: Odebrání elementů, atributů a uzlů ze stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591256"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Odebrání elementů, atributů a uzlů ze stromu XML (C#)

Můžete upravit strom XML, odebrat prvky, atributy a jiné typy uzlů.

Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché. Při odebírání kolekcí prvků nebo atributů byste však měli nejprve vyhodnotit kolekci do seznamu a poté prvky nebo atributy odstranit ze seznamu. Nejlepším řešením je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to provede za vás.

Hlavním důvodem pro toto je to, že většina kolekcí, které načítáte ze stromu XML, je výsledkem použití odloženého provedení. Pokud je nebudete napřed vyhodnotit do seznamu, nebo pokud nepoužíváte rozšiřující metody, je možné narazit na určitou třídu chyb. Další informace naleznete v tématu [smíšený deklarativní kód/nepodmíněný kód chyby (LINQ to XML)C#()](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Následující metody odstraňují uzly a atributy ze stromu XML.

|Metoda|Popis|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XAttribute> Odebere z jeho nadřazeného prvku.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer>.|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odebere obsah a atributy z <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, pak atribut odeberte.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, pak je podřízený element odebrán.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<xref:System.Xml.Linq.XNode> Odebere z jeho nadřazeného prvku.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Odebere všechny atributy nebo elementy ve zdrojové kolekci z jejího nadřazeného prvku.|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Tento příklad ukazuje tři přístupy k odebrání prvků. Nejprve odebere jeden prvek. Za druhé načte kolekci prvků, materializuje je pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátoru a kolekce odebere. Nakonec načte kolekci prvků a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření.

Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru naleznete v tématu [Převod datových typů (C#)](./converting-data-types.md).

### <a name="code"></a>Kód

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

Tento kód generuje následující výstup:

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

Všimněte si, že byl odebrán první podřízený prvek z `Child1`. Všechny prvky podřízené byly odebrány z `Child2` a z. `Child3`
