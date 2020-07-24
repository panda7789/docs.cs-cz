---
title: Porovnání jazyka XPath a technologie LINQ to XML
description: Přečtěte si o podobnostech a rozdílech mezi funkcemi XPath a LINQ to XML v jazyce C#. Pro dotazování stromu XML lze použít obojí.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104009"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porovnání jazyka XPath a technologie LINQ to XML
XPath a LINQ to XML nabízejí podobné funkce. Oba lze použít k dotazování stromu XML a vrácení těchto výsledků jako kolekce prvků, kolekce atributů, kolekce uzlů nebo hodnoty elementu nebo atributu. Existují však i některé rozdíly.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Rozdíly mezi XPath a LINQ to XML  
 XPath nepovoluje projekci nových typů. Může vracet pouze kolekce uzlů ze stromu, zatímco LINQ to XML může spustit dotaz a projekt v grafu objektů nebo stromu XML v novém tvaru. LINQ to XML dotazy zahrnují mnohem více funkcí a jsou mnohem výkonnější než výrazy XPath.  
  
 Výrazy XPath existují v izolaci v rámci řetězce. Kompilátor jazyka C# nemůže v době kompilace přispět k analýze výrazu XPath. Naopak LINQ to XML dotazy jsou analyzovány a kompilovány kompilátorem jazyka C#. Kompilátor je schopný zachytit mnoho chyb dotazů.  
  
 Výsledky XPath nejsou silného typu. V řadě případů je výsledkem vyhodnocení výrazu XPath objekt a je až vývojář, aby určil správný typ a vyhodnotil výsledek podle potřeby. Naopak projekce z LINQ to XML dotazu jsou silného typu.  
  
## <a name="result-ordering"></a>Řazení výsledků  
 Doporučení XPath 1,0 uvádí, že kolekce, která je výsledkem vyhodnocení výrazu XPath, je neuspořádaná.  
  
 Při iteraci kolekcí vrácených LINQ to XML metodou osy XPath však budou uzly v kolekci vráceny v pořadí dokumentů. Jedná se o případ i při přístupu k ose XPath, kde jsou predikáty vyjádřeny na základě objednávky reverzního dokumentu, například `preceding` a `preceding-sibling` .  
  
 Naopak většina z LINQ to XML osy vrací kolekce v pořadí dokumentů, ale dva z nich <xref:System.Xml.Linq.XNode.Ancestors%2A> <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> vrací kolekce v obráceném pořadí dokumentů. V následující tabulce jsou vyhodnoceny osy a jsou známy pořadí shromažďování dat:  
  
|LINQ to XML osa|Řazení|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Pořadí dokumentů|  
|XContainer. Descendants|Pořadí dokumentů|  
|XContainer. Elements|Pořadí dokumentů|  
|XContainer. Nodes|Pořadí dokumentů|  
|XContainer.NodesAfterSelf|Pořadí dokumentů|  
|XContainer.NodesBeforeSelf|Pořadí dokumentů|  
|XElement. AncestorsAndSelf|Obrátit objednávku dokumentu|  
|XElement. Attributes|Pořadí dokumentů|  
|XElement. DescendantNodesAndSelf|Pořadí dokumentů|  
|XElement. DescendantsAndSelf|Pořadí dokumentů|  
|XNode. nadřazených prvků|Obrátit objednávku dokumentu|  
|XNode.ElementsAfterSelf|Pořadí dokumentů|  
|XNode.ElementsBeforeSelf|Pořadí dokumentů|  
|XNode.NodesAfterSelf|Pořadí dokumentů|  
|XNode.NodesBeforeSelf|Pořadí dokumentů|  
  
## <a name="positional-predicates"></a>Poziční predikáty  
 V rámci výrazu XPath jsou poziční predikáty vyjádřeny v pořadí dokumentů pro mnoho OS, ale jsou vyjádřeny v obráceném pořadí dokumentů pro reverzní osy, které jsou `preceding` , `preceding-sibling` , `ancestor` a `ancestor-or-self` . Například výraz XPath `preceding-sibling::*[1]` vrátí přímo předchozí položku na stejné úrovni. To platí i v případě, že výsledná sada výsledků je prezentována v pořadí dokumentů.  
  
 Naopak všechny poziční predikáty v LINQ to XML jsou vždy vyjádřeny v pořadí podle pořadí osy. Například `anElement.ElementsBeforeSelf().ElementAt(0)` vrátí první podřízený prvek nadřazeného elementu s dotazem, nikoli bezprostřední předchozí uzel na stejné úrovni. Jiný příklad: `anElement.Ancestors().ElementAt(0)` Vrátí nadřazený element.  
  
 Pokud jste chtěli najít bezprostředně předchozí prvek v LINQ to XML, měli byste napsat následující výraz:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Rozdíly v výkonu  
 Dotazy XPath, které používají funkci XPath v LINQ to XML, nebudou provádět ani dotazy LINQ to XML.  
  
## <a name="comparison-of-composition"></a>Porovnání složení  
 Složení LINQ to XMLho dotazu je trochu paralelní na složení výrazu XPath, i když je v syntaxi velmi odlišné.  
  
 Například pokud máte prvek v proměnné s názvem `customers` a chcete najít podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer` , měli byste napsat výraz XPath následujícím způsobem:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Ekvivalentní LINQ to XML dotaz:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Pro každou osu XPath existují podobné paralelismuy.  
  
|Osa XPath|LINQ to XML osa|  
|----------------|----------------------|  
|podřízená (výchozí osa)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadřazený objekt (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|osa atributu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> nebo<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|Nadřazená osa|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|nadřazený nebo samoobslužná osa|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|osa následníka (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> nebo<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|následník – nebo – samotný|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> nebo<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|po stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> nebo<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|předchozí uzel na stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> nebo<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|důsledku|Žádný přímý ekvivalent.|  
|cházel|Žádný přímý ekvivalent.|  
  