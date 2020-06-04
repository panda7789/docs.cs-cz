---
title: Odebrání elementů, atributů a uzlů ze stromu XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413401"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Odebrání elementů, atributů a uzlů ze stromu XML (Visual Basic)
Můžete upravit strom XML, odebrat prvky, atributy a jiné typy uzlů.  
  
 Odebrání jednoho prvku nebo jednoho atributu z dokumentu XML je jednoduché. Při odebírání kolekcí prvků nebo atributů byste však měli nejprve vyhodnotit kolekci do seznamu a poté prvky nebo atributy odstranit ze seznamu. Nejlepším řešením je použít <xref:System.Xml.Linq.Extensions.Remove%2A> metodu rozšíření, která to provede za vás.  
  
 Hlavním důvodem pro toto je to, že většina kolekcí, které načítáte ze stromu XML, je výsledkem použití odloženého provedení. Pokud je nebudete napřed vyhodnotit do seznamu, nebo pokud nepoužíváte rozšiřující metody, je možné narazit na určitou třídu chyb. Další informace naleznete v tématu [smíšený deklarativní kód/nepodmíněný kód chyby (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Následující metody odstraňují uzly a atributy ze stromu XML.  
  
|Metoda|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XAttribute> z jeho nadřazeného prvku.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Odebere podřízené uzly z <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Odebere obsah a atributy z <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Odebere atributy <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, pak atribut odeberte.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Pokud předáte `null` hodnotu, pak je podřízený element odebrán.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Odebere <xref:System.Xml.Linq.XNode> z jeho nadřazeného prvku.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Odebere všechny atributy nebo elementy ve zdrojové kolekci z jejího nadřazeného prvku.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Description  
 Tento příklad ukazuje tři přístupy k odebrání prvků. Nejprve odebere jeden prvek. Za druhé načte kolekci prvků, materializuje je pomocí <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operátoru a kolekce odebere. Nakonec načte kolekci prvků a odebere je pomocí <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozšíření.  
  
 Další informace o <xref:System.Linq.Enumerable.ToList%2A> operátoru naleznete v tématu [Převod datových typů (Visual Basic)](converting-data-types.md).  
  
### <a name="code"></a>Kód  
  
```vb  
Dim root As XElement = _  
    <Root>  
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
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
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
  
 Všimněte si, že byl odebrán první podřízený prvek z `Child1` . Všechny prvky podřízené byly odebrány z `Child2` a z `Child3` .  
  
## <a name="see-also"></a>Viz také

- [Úprava stromů XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
