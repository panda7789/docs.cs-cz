---
title: LinQ na XML osy Přehled (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: c8b64731925f37d54bded62fae4ccae9933ffbe9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635519"
---
# <a name="linq-to-xml-axes-overview-c"></a>LinQ na XML osy Přehled (C#)
Po vytvoření stromu XML nebo naložení dokumentu XML do stromu XML můžete jej zadat dotazem, abyste našli prvky a atributy a načetli jejich hodnoty. Kolekce načtete prostřednictvím *metod osy*, nazývaných také *osy*. Některé osy jsou metody <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> v a <xref:System.Collections.Generic.IEnumerable%601> třídy, které vracejí kolekce. Některé z os jsou rozšiřující <xref:System.Xml.Linq.Extensions> metody ve třídě. Osy, které jsou implementovány jako metody rozšíření pracovat na kolekce a návrat kolekce.  
  
 Jak je popsáno v Přehled <xref:System.Xml.Linq.XElement> [třídy XElement](./xelement-class-overview.md), objekt představuje uzel jednoho prvku. Obsah prvku může být složitý (někdy nazývaný strukturovaný obsah) nebo může být jednoduchý prvek. Jednoduchý prvek může být prázdný nebo může obsahovat hodnotu. Pokud uzel obsahuje strukturovaný obsah, můžete použít různé metody osy k načtení výčtů potomků prvků. Nejčastěji používané metody osy jsou <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Kromě metody osy, které vracejí kolekce, existují další dvě metody, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] které budete běžně používat v dotazech. Metoda <xref:System.Xml.Linq.XContainer.Element%2A> vrátí jeden <xref:System.Xml.Linq.XElement>. Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> vrátí jeden <xref:System.Xml.Linq.XAttribute>.  
  
 Pro mnoho účelů linq dotazy poskytují nejúčinnější způsob, jak prozkoumat strom, extrahovat data z něj a transformovat ji. LINQ dotazy pracovat na <xref:System.Collections.Generic.IEnumerable%601>objekty, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] které <xref:System.Collections.Generic.IEnumerable%601> implementují a <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> osy vrácení <xref:System.Xml.Linq.XElement> kolekcí a kolekcí. Tyto kolekce potřebujete k provádění dotazů.  
  
 Kromě metody osy, které načítají kolekce prvků a atributů, existují metody osy, které umožňují iterate přes strom velmi podrobně. Například místo práce s prvky a atributy, můžete pracovat s uzly stromu. Uzly jsou jemnější úroveň rozlišovací schopnost než prvky a atributy. Při práci s uzly můžete prozkoumat komentáře XML, textové uzly, pokyny pro zpracování a další. Tato funkce je důležitá například pro uživatele, který píše textový procesor a chce uložit dokumenty jako XML. Většina programátorů XML se však primárně zabývá prvky, atributy a jejich hodnotami.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro načítání kolekce prvků  
 Následuje souhrn metod <xref:System.Xml.Linq.XElement> třídy (nebo její základní třídy), které <xref:System.Xml.Linq.XElement> voláte na vrátit kolekci prvků.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> z předchůdce tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> předchůdce, <xref:System.Xml.Linq.XElement> které mají zadané <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> z potomků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> descendants, <xref:System.Xml.Linq.XElement> které mají zadaný <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> podřízené <xref:System.Xml.Linq.XElement> prvky tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> podřízené <xref:System.Xml.Linq.XElement> prvky, které <xref:System.Xml.Linq.XName>mají zadané .|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> prvky, <xref:System.Xml.Linq.XElement> které přicházejí po tento prvek. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> prvků <xref:System.Xml.Linq.XElement> po tento prvek, které <xref:System.Xml.Linq.XName>mají zadaný .|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> prvky, <xref:System.Xml.Linq.XElement> které jsou před tímto prvkem. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> prvků <xref:System.Xml.Linq.XElement> před tento prvek, které <xref:System.Xml.Linq.XName>mají zadaný .|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> tohoto prvku a jeho předchůdce. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> prvků, které mají <xref:System.Xml.Linq.XName>zadané .|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> tohoto prvku a jeho potomky. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XElement> prvků, které mají <xref:System.Xml.Linq.XName>zadané .|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda načítání jednoho prvku  
 Následující metoda načte jeden podřízený z objektu. <xref:System.Xml.Linq.XElement>  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrátí první <xref:System.Xml.Linq.XElement> podřízený objekt, <xref:System.Xml.Linq.XName>který má zadaný .|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda načítání kolekce atributů  
 Následující metoda načte atributy <xref:System.Xml.Linq.XElement> z objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> hodnotu <xref:System.Xml.Linq.XAttribute> všech atributů.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda načítání jednoho atributu  
 Následující metoda načte jeden atribut <xref:System.Xml.Linq.XElement> z objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí <xref:System.Xml.Linq.XAttribute> soubor, který <xref:System.Xml.Linq.XName>má zadaný soubor .|  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](linq-to-xml-axes-overview.md)
