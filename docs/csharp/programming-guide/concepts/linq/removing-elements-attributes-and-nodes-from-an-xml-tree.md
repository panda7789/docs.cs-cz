---
title: Odebrání elementů, atributů a uzlů ze stromu XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217487"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Odebrání elementů, atributů a uzlů ze stromu XML (C#)
Můžete upravit stromu XML, odebrání elementů, atributů a dalších typů uzlů.  
  
 Odebrání jeden element nebo jeden atribut z dokumentu XML je jednoduché. Ale při odstraňování kolekce elementy nebo atributy, musí nejprve sloučit kolekci do seznamu a pak odstraníte elementy nebo atributy ze seznamu. Nejlepší možností je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to udělal za vás.  
  
 Hlavním důvodem pro to je, že jsou výsledkem většinu kolekce, které se načítají ze stromu XML pomocí odloženého provedení. Pokud jste není nejprve materializovat je do seznamu, nebo pokud používáte metody rozšíření, je možné se setkat se třídy chyb. Další informace najdete v tématu [smíšené deklarativní kód/dnešní kód chyby (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Následující metody odebrání uzlů a atributy ze stromu XML.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XAttribute> od svého nadřazeného objektu.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Odebere podřízené uzly ze <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odstraní obsah a atributy ze <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Pokud předáte `null` pro hodnotu, pak taky odebere atribut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Pokud předáte `null` pro hodnotu, pak taky odebere podřízený element.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XNode> od svého nadřazeného objektu.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Odebere každý atribut nebo element ve zdrojové kolekci ze svého nadřízeného elementu.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje tři přístupy k odebrání prvků. Nejprve se odebere jeden element. Za druhé, načte kolekci elementů, bude je realizována pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátorů a odebere kolekce. A konečně, načte kolekci elementů a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> – metoda rozšíření.  
  
 Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru, naleznete v tématu [převádění datových typů (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).  
  
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
 Tento kód vytvoří následující výstup:  
  
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
  
 Všimněte si, že první podřízený element byl odebrán z `Child1`. Všechny podřízené prvky byly odebrány z `Child2` a z `Child3`.  
  
## <a name="see-also"></a>Viz také

- [Změna stromů XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
