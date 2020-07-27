---
title: Přehled OS LINQ to XML (C#)
description: Přečtěte si o metodách osy v jazyce C#, označovaných také jako osy. Můžete zadat dotaz na strom XML ve výrazu LINQ pro vyhledání prvků a atributů a načtení jejich hodnot přes osy.
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: bbda844e8cb2e3b1ff116fd834c6ab1fdd20c1f8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165447"
---
# <a name="linq-to-xml-axes-overview-c"></a>Přehled OS LINQ to XML (C#)
Po vytvoření stromu XML nebo načtení dokumentu XML do stromu XML můžete zadat dotaz na nalezení prvků a atributů a načíst jejich hodnoty. Kolekce se načítají přes *metody osy*, označované také jako *osy*. Některé osy jsou metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a, které vracejí <xref:System.Collections.Generic.IEnumerable%601> kolekce. Některé osy jsou rozšiřující metody ve <xref:System.Xml.Linq.Extensions> třídě. Osy, které jsou implementovány jako metody rozšíření, pracují na kolekcích a vracejí kolekce.  
  
 Jak je popsáno v [přehledu třídy XElement](./xelement-class-overview.md), <xref:System.Xml.Linq.XElement> objekt představuje jeden uzel elementu. Obsah elementu může být komplexní (někdy označovaný jako strukturovaný obsah), nebo může být jednoduchým prvkem. Jednoduchý element může být prázdný nebo může obsahovat hodnotu. Pokud uzel obsahuje strukturovaný obsah, můžete použít různé metody osy k načtení výčtů následníků. Nejběžněji používané metody osy jsou <xref:System.Xml.Linq.XContainer.Elements%2A> a <xref:System.Xml.Linq.XContainer.Descendants%2A> .  
  
 Kromě metod osy, které vracejí kolekce, existují dvě další metody, které v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazech často používáte. <xref:System.Xml.Linq.XContainer.Element%2A>Metoda vrací hodnotu Single <xref:System.Xml.Linq.XElement> . <xref:System.Xml.Linq.XElement.Attribute%2A>Metoda vrací hodnotu Single <xref:System.Xml.Linq.XAttribute> .  
  
 Pro mnoho účelů LINQ dotazy poskytují nejúčinnější způsob, jak kontrolovat strom, extrahovat z něj data a transformovat ho. Dotazy LINQ pracují na objektech, které implementují <xref:System.Collections.Generic.IEnumerable%601> , a na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osách vrací <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekce <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XAttribute> kolekce. Tyto kolekce budete potřebovat k provádění dotazů.  
  
 Kromě metod osy, které načítají kolekce prvků a atributů, existují metody osy, které umožňují iterovat ve stromové struktuře Skvělé podrobnosti. Například místo řešení prvků a atributů můžete pracovat s uzly stromu. Uzly jsou jemnějším stupněm členitosti než prvky a atributy. Při práci s uzly můžete prozkoumávat komentáře XML, textové uzly, instrukce pro zpracování a další. Tato funkce je důležitá, například pro někoho, kdo napisuje textový procesor a chce uložit dokumenty jako XML. Většina programátorů XML je však primárně dotčena prvky, atributy a jejich hodnotami.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro načtení kolekce prvků  
 Následuje souhrn metod <xref:System.Xml.Linq.XElement> třídy (nebo jejích základních tříd), které zavoláte <xref:System.Xml.Linq.XElement> pro vrácení kolekce prvků.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> nadřazených prvků tohoto prvku. Přetížení vrátí sadu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadřazených prvků, které mají zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> ze <xref:System.Xml.Linq.XElement> následníků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> od <xref:System.Xml.Linq.XElement> následníků, které mají zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízených prvků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízených elementů, které mají zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrátí prvek <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které jsou zadány po tomto prvku. Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků za tímto prvkem, který má zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které jsou zadány před tímto prvkem. Přetížení vrátí prvek <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků před tímto prvkem, který má zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tohoto prvku a jeho nadřazených prvků. Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tohoto prvku a jeho následníků. Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pro načtení jednoho elementu  
 Následující metoda načte jeden podřízený <xref:System.Xml.Linq.XElement> objekt z objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrátí první podřízený <xref:System.Xml.Linq.XElement> objekt, který má zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pro načtení kolekce atributů  
 Následující metoda načte atributy z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> ze <xref:System.Xml.Linq.XAttribute> všech atributů.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pro načtení jednoho atributu  
 Následující metoda načte jeden atribut z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí <xref:System.Xml.Linq.XAttribute> , který má zadanou hodnotu <xref:System.Xml.Linq.XName> .|  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](linq-to-xml-axes-overview.md)
