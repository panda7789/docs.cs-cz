---
title: Porovnání jazyka XPath a technologie LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: f41aa19c89365c9236ca0b8d385ffa6fbaf6be1c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391733"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porovnání jazyka XPath a technologie LINQ to XML
Výraz XPath a technologie LINQ to XML nabízejí některé podobné funkce. Jak lze použít k dotazování stromu XML, vrátí tyto výsledky jako kolekci elementů, kolekce atributů, kolekce uzlů nebo hodnotu elementu nebo atributu. Existují však také několik rozdílů.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Rozdíly mezi XPath a technologie LINQ to XML  
 Výraz XPath není povolena projekce nových typů. To může vrátit pouze kolekce uzlů ze stromu, zatímco LINQ to XML můžete spustit dotaz a projekt grafu objektu nebo stromu XML v nový tvar. Technologie LINQ to XML dotazů zvětšíte mnohem víc funkcí a jsou výrazně výkonnější než výrazy XPath.  
  
 Výrazy XPath existovat samostatně v rámci řetězce. Kompilátor jazyka C# vám nemůže pomoci parsovat výraz XPath v době kompilace. Naopak LINQ to XML dotazy jsou analyzovány a zkompilovány kompilátorem jazyka C#. Kompilátoru je moci zachytávat chyby mnoho dotazů.  
  
 Výraz XPath výsledky nejsou silného typu. V počtu situací je výsledkem vyhodnocení výrazu XPath objektu a je vývojářům určit správný typ a přetypujte výsledek podle potřeby. Naopak projekce v LINQ dotazu XML jsou silného typu.  
  
## <a name="result-ordering"></a>Výsledek řazení  
 Výraz XPath 1.0 doporučení uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath Neseřazený.  
  
 Ale když iterace v kolekci vrácené LINQ metody osy XML XPath, uzly v kolekci jsou vráceny v pořadí dokumentů. To platí i v případě, že přístup k osy XPath kde predikáty se vyjadřují v pořadí reverzní dokumentů, jako například `preceding` a `preceding-sibling`.  
  
 Naopak většina technologie LINQ to XML osy vrací kolekce v pořadí dokumentů, ale dva z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, vrací kolekce v pořadí reverzní dokumentů. V následující tabulce vytvoří výčet OS a určuje pořadí kolekce pro jednotlivé:  
  
|Technologie LINQ to XML – osa|Řazení|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Pořadí dokumentů|  
|XContainer.Descendants|Pořadí dokumentů|  
|XContainer.Elements|Pořadí dokumentů|  
|XContainer.Nodes|Pořadí dokumentů|  
|XContainer.NodesAfterSelf|Pořadí dokumentů|  
|XContainer.NodesBeforeSelf|Pořadí dokumentů|  
|XElement.AncestorsAndSelf|Pořadí reverzní dokumentů|  
|XElement.Attributes|Pořadí dokumentů|  
|XElement.DescendantNodesAndSelf|Pořadí dokumentů|  
|XElement.DescendantsAndSelf|Pořadí dokumentů|  
|XNode.Ancestors|Pořadí reverzní dokumentů|  
|XNode.ElementsAfterSelf|Pořadí dokumentů|  
|XNode.ElementsBeforeSelf|Pořadí dokumentů|  
|XNode.NodesAfterSelf|Pořadí dokumentů|  
|XNode.NodesBeforeSelf|Pořadí dokumentů|  
  
## <a name="positional-predicates"></a>Poziční predikáty.  
 Ve výrazu XPath poziční predikáty se vyjadřují v pořadí dokumentů pro mnoho osy, ale jsou vyjádřeny v pořadí reverzní dokumentů pro reverzní osy, které jsou `preceding`, `preceding-sibling`, `ancestor`, a `ancestor-or-self`. Například výraz XPath `preceding-sibling::*[1]` vrátí bezprostředně předcházející na stejné úrovni. To platí i v případě, že sada konečný výsledek se zobrazí v pořadí dokumentů.  
  
 Naopak všechny predikáty poziční v technologii LINQ to XML se vždy vyjadřují v pořadí osy. Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený element nadřazeného elementu poslal dotaz, ne okamžité předcházející na stejné úrovni. Další příklad: `anElement.Ancestors().ElementAt(0)` vrátí nadřazeného elementu.  
  
 Pokud byste chtěli najít bezprostředně předcházející prvek v technologii LINQ to XML, měli byste napsat následující výraz:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Rozdíly ve výkonu  
 Dotazy XPath, které používají funkce XPath v technologii LINQ to XML nebude provádět, tak LINQ dotazy XML.  
  
## <a name="comparison-of-composition"></a>Porovnání složení  
 Složení LINQ to XML dotazu je poněkud paralelní složení výraz XPath, ale velmi odlišné v syntaxi.  
  
 Například, pokud máte v proměnné s názvem elementu `customers`, a vy chcete najít podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer`, měli byste napsat výraz XPath následujícím způsobem:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Je ekvivalentní LINQ to XML dotazu:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Jsou podobné parallels pro každý OS XPath.  
  
|Výraz XPath osy|Technologie LINQ to XML – osa|  
|----------------|----------------------|  
|podřízený (na ose výchozí)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadřazené (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|atribut osy (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|předchůdce osy|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|předchůdce nebo self OS|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|Následnické osy (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|Následující na stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|předcházející na stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Následující|Žádný přímý ekvivalent.|  
|předchozí|Žádný přímý ekvivalent.|  
  
## <a name="see-also"></a>Viz také  
 [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
