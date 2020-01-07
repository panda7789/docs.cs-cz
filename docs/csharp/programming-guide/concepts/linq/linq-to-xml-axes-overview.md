---
title: Přehled OS LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: c8b64731925f37d54bded62fae4ccae9933ffbe9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635519"
---
# <a name="linq-to-xml-axes-overview-c"></a>Přehled OS LINQ to XML (C#)
Po vytvoření stromu XML nebo načtení dokumentu XML do stromu XML můžete zadat dotaz na nalezení prvků a atributů a načíst jejich hodnoty. Kolekce se načítají přes *metody osy*, označované také jako *osy*. Některé osy jsou metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy, které vracejí <xref:System.Collections.Generic.IEnumerable%601> kolekce. Některé osy jsou rozšiřující metody ve třídě <xref:System.Xml.Linq.Extensions>. Osy, které jsou implementovány jako metody rozšíření, pracují na kolekcích a vracejí kolekce.  
  
 Jak je popsáno v [přehledu třídy XElement](./xelement-class-overview.md), objekt <xref:System.Xml.Linq.XElement> představuje uzel s jedním elementem. Obsah elementu může být komplexní (někdy označovaný jako strukturovaný obsah), nebo může být jednoduchým prvkem. Jednoduchý element může být prázdný nebo může obsahovat hodnotu. Pokud uzel obsahuje strukturovaný obsah, můžete použít různé metody osy k načtení výčtů následníků. Nejběžněji používané metody osy jsou <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Kromě metod osy, které vrací kolekce, existují dvě další metody, které se běžně používají v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazů. Metoda <xref:System.Xml.Linq.XContainer.Element%2A> vrací jeden <xref:System.Xml.Linq.XElement>. Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> vrací jeden <xref:System.Xml.Linq.XAttribute>.  
  
 Pro mnoho účelů LINQ dotazy poskytují nejúčinnější způsob, jak kontrolovat strom, extrahovat z něj data a transformovat ho. Dotazy LINQ pracují na objektech, které implementují <xref:System.Collections.Generic.IEnumerable%601>, a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] OS vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekcí a <xref:System.Collections.Generic.IEnumerable%601> kolekcí <xref:System.Xml.Linq.XAttribute>. Tyto kolekce budete potřebovat k provádění dotazů.  
  
 Kromě metod osy, které načítají kolekce prvků a atributů, existují metody osy, které umožňují iterovat ve stromové struktuře Skvělé podrobnosti. Například místo řešení prvků a atributů můžete pracovat s uzly stromu. Uzly jsou jemnějším stupněm členitosti než prvky a atributy. Při práci s uzly můžete prozkoumávat komentáře XML, textové uzly, instrukce pro zpracování a další. Tato funkce je důležitá, například pro někoho, kdo napisuje textový procesor a chce uložit dokumenty jako XML. Většina programátorů XML je však primárně dotčena prvky, atributy a jejich hodnotami.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro načtení kolekce prvků  
 Následuje souhrn metod <xref:System.Xml.Linq.XElement> třídy (nebo jejích základních tříd), které zavoláte na <xref:System.Xml.Linq.XElement> pro vrácení kolekce prvků.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadřazených prvků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadřazených prvků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> potomků tohoto prvku. Přetížení vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> potomků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> podřízených prvků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> podřízených prvků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků, které jsou zadány po tomto elementu. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků za tímto prvkem, který má zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků, které jsou zadány před tímto prvkem. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků před tímto prvkem, který má zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tohoto prvku a jeho nadřazených prvků. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tohoto prvku a jeho následníků. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> prvků, které mají zadanou <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pro načtení jednoho elementu  
 Následující metoda načte jeden podřízený objekt z objektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrátí první podřízený objekt <xref:System.Xml.Linq.XElement>, který má zadaný <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pro načtení kolekce atributů  
 Následující metoda načte atributy z objektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> všech atributů.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pro načtení jednoho atributu  
 Následující metoda načte jeden atribut z objektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí <xref:System.Xml.Linq.XAttribute>, který má zadanou <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](linq-to-xml-axes-overview.md)
