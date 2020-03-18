---
title: Porovnání jazyka XPath a technologie LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487541"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porovnání jazyka XPath a technologie LINQ to XML
XPath a LINQ na XML nabízejí některé podobné funkce. Oba lze použít k dotazování stromu XML, vrácení takové výsledky jako kolekce prvků, kolekce atributů, kolekce uzlů nebo hodnota prvku nebo atributu. Existují však také určité rozdíly.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Rozdíly mezi XPath a LINQ na XML  
 XPath neumožňuje projekci nových typů. Může vrátit pouze kolekce uzlů ze stromu, zatímco LINQ do XML může spustit dotaz a promítnout objektový graf nebo strom XML v novém obrazci. Dotazy LINQ na XML zahrnují mnohem více funkcí a jsou mnohem výkonnější než výrazy XPath.  
  
 Výrazy XPath existují izolovaně v rámci řetězce. Kompilátor Jazyka C# nemůže pomoci analyzovat výraz XPath v době kompilace. Naproti tomu linq na XML dotazy jsou analyzovány a kompilovány kompilátorem Jazyka C#. Kompilátor je schopen zachytit mnoho chyb dotazu.  
  
 Výsledky XPath nejsou silně zadány. V řadě okolností je výsledkem vyhodnocení výrazu XPath objekt a je na vývojáři, aby určil správný typ a podle potřeby přetypoval výsledek. Naproti tomu projekce z linq do dotazu XML jsou silně zadávány.  
  
## <a name="result-ordering"></a>Pořadí výsledků  
 Doporučení XPath 1.0 uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath je neuspořádané.  
  
 Však při iterace prostřednictvím kolekce vrácené LINQ na XML XPath osy metody, uzly v kolekci jsou vráceny v pořadí dokumentů. To platí i při přístupu k osám XPath, kde jsou predikáty vyjádřeny obráceným pořadím dokumentů, například `preceding` a `preceding-sibling`.  
  
 Naproti tomu většina os LINQ do XML vrací kolekce v pořadí <xref:System.Xml.Linq.XNode.Ancestors%2A> <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>dokumentů, ale dvě z nich a , vrátí kolekce v obráceném pořadí dokumentů. Následující tabulka obsahuje výčet os a označuje pořadí sběru pro každou z nich:  
  
|LinQ na osu XML|Řazení|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Pořadí dokumentů|  
|XContainer.Descendants|Pořadí dokumentů|  
|XKontejner.Elements|Pořadí dokumentů|  
|XContainer.Uzly|Pořadí dokumentů|  
|XContainer.NodesAfterSelf|Pořadí dokumentů|  
|XContainer.NodesBeforeSelf|Pořadí dokumentů|  
|XElement.AncestorsAndSelf|Obrácené pořadí dokumentů|  
|XElement.Atributy|Pořadí dokumentů|  
|XElement.DescendantNodesAndSelf|Pořadí dokumentů|  
|XElement.DescendantsAndSelf|Pořadí dokumentů|  
|XNode.Předkové|Obrácené pořadí dokumentů|  
|XNode.ElementsAfterSelf|Pořadí dokumentů|  
|XNode.ElementsBeforeSelf|Pořadí dokumentů|  
|XNode.NodesAfterSelf|Pořadí dokumentů|  
|XNode.NodesBeforeSelf|Pořadí dokumentů|  
  
## <a name="positional-predicates"></a>Poziční predikáty  
 V rámci výrazu XPath jsou poziční predikáty vyjádřeny v pořadí dokumentů pro mnoho os, ale `preceding` `preceding-sibling`jsou `ancestor`vyjádřeny v obráceném pořadí dokumentů pro reverzní osy, které jsou , , , a `ancestor-or-self`. Například výraz `preceding-sibling::*[1]` XPath vrátí bezprostředně předcházející na stejné úrovni. To je případ i v případě, že konečná sada výsledků je uveden v pořadí dokumentů.  
  
 Naproti tomu všechny poziční predikáty v LINQ na XML jsou vždy vyjádřeny v pořadí osy. Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený prvek nadřazeného prvku dotazovaného prvku, nikoli bezprostředně předcházející na stejné úrovni. Jiný příklad: `anElement.Ancestors().ElementAt(0)` vrátí nadřazený prvek.  
  
 Pokud byste chtěli najít bezprostředně předcházející prvek v LINQ do XML, napsali byste následující výraz:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Rozdíly ve výkonu  
 Dotazy XPath, které používají funkci XPath v LINQ na XML, nebudou fungovat tak dobře jako linq na dotazy XML.  
  
## <a name="comparison-of-composition"></a>Porovnání složení  
 Složení dotazu LINQ na XML je poněkud paralelní se složením výrazu XPath, i když se velmi liší syntaxí.  
  
 Například pokud máte prvek v proměnné `customers`s názvem , a chcete `CompanyName` najít prvek vnouče s názvem pod všechny podřízené prvky s názvem `Customer`, byste napsat výraz XPath takto:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Ekvivalentní linq dotazu XML je:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Existují podobné paralely pro každou z os XPath.  
  
|Osa XPath|LinQ na osu XML|  
|----------------|----------------------|  
|podřízená (výchozí osa)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Rodič (..)od rodičů (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|osa atributu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> – nebo –<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|předek osa|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|předek-nebo-vlastní osa|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|následná osa (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> – nebo –<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|potomek-nebo-já|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> – nebo –<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|následující-sourozenec|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> – nebo –<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|předchozí-sourozenec|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> – nebo –<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Následující|Žádný přímý ekvivalent.|  
|Předchozí|Žádný přímý ekvivalent.|  
  