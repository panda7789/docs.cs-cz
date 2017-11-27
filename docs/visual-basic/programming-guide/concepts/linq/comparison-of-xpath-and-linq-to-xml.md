---
title: "Porovnání jazyka XPath a v technologii LINQ to XML1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 761df14ee4bdfa9ddeb3f742134f4f47f8bb283f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porovnání jazyka XPath a technologie LINQ to XML
Výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nabízejí některé podobné funkce. Obě lze použít k dotazu strom XML vrácení takové výsledky jako kolekci elementů, kolekce atributů, kolekce uzlů nebo hodnota elementu nebo atributu. Existují však také některé rozdíly.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Rozdíly mezi XPath a LINQ to XML  
 Výraz XPath neumožňuje projekce nových typů. Ho může vrátit pouze kolekce uzlů ze stromu, zatímco [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může provést dotaz a projekt grafu objektu nebo strom XML v nový tvar. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dotazy zahrnovat mnohem víc funkcí a jsou mnohem silnější než výrazech XPath.  
  
 Výrazech XPath existovat v izolaci v řetězci. Visual Basic – kompilátor nemůže pomoct analyzovat výraz XPath v době kompilace. Naopak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy jsou analyzovat a zkompilují theVisual základní kompilátoru. Kompilátor je schopen zachycení mnoho chyb dotazu.  
  
 XPath výsledky nejsou silného typu. Počet okolností výsledkem vyhodnocení výrazu jazyka XPath je objekt a je na vývojáře a určit správný typ přetypování výsledek podle potřeby. Naopak projekce z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu jsou silného typu.  
  
## <a name="result-ordering"></a>Způsobit řazení  
 Doporučení 1.0 XPath uvádí, že neuspořádaného kolekce, která je výsledkem vyhodnocení výrazu XPath.  
  
 Ale když iterace v kolekci vrácený [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath metoda osy, uzly v kolekci jsou vráceny v pořadí dokumentů. To platí i v případě, že přístup k ose XPath kde predikáty jsou uvedeny z hlediska pořadí zpětné dokumentů, jako například `preceding` a `preceding-sibling`.  
  
 Podle naproti tomu většina [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osy vrátí kolekce v pořadí dokumentu, ale dvě z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, vrátí kolekce v pořadí zpětné dokumentů. V následující tabulce vytvoří výčet osy a určuje pořadí kolekce pro každou:  
  
|Technologie LINQ to XML – osa|Řazení|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Pořadí dokumentů|  
|XContainer.Descendants|Pořadí dokumentů|  
|XContainer.Elements|Pořadí dokumentů|  
|XContainer.Nodes|Pořadí dokumentů|  
|XContainer.NodesAfterSelf|Pořadí dokumentů|  
|XContainer.NodesBeforeSelf|Pořadí dokumentů|  
|XElement.AncestorsAndSelf|Reverse pořadí dokumentů|  
|XElement.Attributes|Pořadí dokumentů|  
|XElement.DescendantNodesAndSelf|Pořadí dokumentů|  
|XElement.DescendantsAndSelf|Pořadí dokumentů|  
|XNode.Ancestors|Reverse pořadí dokumentů|  
|XNode.ElementsAfterSelf|Pořadí dokumentů|  
|XNode.ElementsBeforeSelf|Pořadí dokumentů|  
|XNode.NodesAfterSelf|Pořadí dokumentů|  
|XNode.NodesBeforeSelf|Pořadí dokumentů|  
  
## <a name="positional-predicates"></a>Poziční predikáty  
 V rámci výrazu jazyka XPath poziční predikáty jsou vyjádřeny z hlediska pořadí dokumentů pro mnoho osy, ale jsou vyjádřeny v pořadí zpětné dokumentů pro zpětné osy, které jsou `preceding`, `preceding-sibling`, `ancestor`, a `ancestor-or-self`. Například výraz XPath `preceding-sibling::*[1]` vrátí poslední položku na stejné úrovni. Jde o případ, i když sadu konečný výsledek je seřazen podle dokumentu.  
  
 Naopak všechny poziční predikáty v technologii LINQ to XML vždy vyjádřeny z hlediska pořadí osy. Například `anElement.ElementsBeforeSelf().ToList()[0]` vrátí první podřízený prvek nadřazeného prvku předmětem dotazu není okamžitý předchozí položky. Jiný příklad: `anElement.Ancestors().ToList()[0]` vrátí nadřazeného elementu.  
  
 Všimněte si, že bude výše uvedený přístup realizována celou kolekci. Nejedná se o nejúčinnější způsob, jak k zápisu tohoto dotazu. Byl soubor napsaný v tímto způsobem k předvedení chování poziční predikáty. Více vhodný způsob k zápisu stejný dotaz se má používat <xref:System.Linq.Enumerable.First%2A> metoda následujícím způsobem: `anElement.ElementsBeforeSelf().First()`.  
  
 Pokud chcete najít okamžitě předchozí element v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], byste měli psát následující výraz:  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Rozdíly výkonu  
 Výraz XPath dotazy, které používají funkci XPath v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nebude provádět a také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.  
  
## <a name="comparison-of-composition"></a>Porovnání složení  
 Složení [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz je poněkud paralelní k složení výraz XPath, i když se příliš neliší v syntaxi.  
  
 Například, pokud máte v proměnné s názvem elementu `customers`, a chcete najít pod podřízený element s názvem `CompanyName` v rámci všech podřízených elementů s názvem `Customer`, byste měli psát výraz XPath následujícím způsobem:  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 Ekvivalent [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz je:  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 Existují podobné parallels pro každou z OS XPath.  
  
|Výraz XPath osy|Technologie LINQ to XML – osa|  
|----------------|----------------------|  
|podřízené (na ose výchozí)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadřazené (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|osa atributu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|nadřazené osy|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|nadřazené or-self osy|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|osy nástupce (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|Následující na stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|předcházející na stejné úrovni|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Následující|Ekvivalent.|  
|předcházející|Ekvivalent.|  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML pro uživatele XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
