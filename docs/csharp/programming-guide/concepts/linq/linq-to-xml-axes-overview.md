---
title: Přehled OS LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: b775a37869f0c8baa7d482475e301347cb77c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591919"
---
# <a name="linq-to-xml-axes-overview-c"></a>Přehled OS LINQ to XML (C#)
Po vytvoření stromu XML nebo načtení dokumentu XML do stromu XML můžete zadat dotaz na nalezení prvků a atributů a načíst jejich hodnoty. Kolekce se načítají přes *metody osy*, označované také jako *osy*. Některé osy jsou metody v <xref:System.Xml.Linq.XElement> třídách a <xref:System.Xml.Linq.XDocument> , které vracejí <xref:System.Collections.Generic.IEnumerable%601> kolekce. Některé osy jsou rozšiřující metody ve <xref:System.Xml.Linq.Extensions> třídě. Osy, které jsou implementovány jako metody rozšíření, pracují na kolekcích a vracejí kolekce.  
  
 Jak je popsáno v [přehledu třídy XElement](./xelement-class-overview.md), <xref:System.Xml.Linq.XElement> objekt představuje jeden uzel elementu. Obsah elementu může být komplexní (někdy označovaný jako strukturovaný obsah), nebo může být jednoduchým prvkem. Jednoduchý element může být prázdný nebo může obsahovat hodnotu. Pokud uzel obsahuje strukturovaný obsah, můžete použít různé metody osy k načtení výčtů následníků. Nejběžněji používané metody osy jsou <xref:System.Xml.Linq.XContainer.Elements%2A> a. <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
 Kromě metod osy, které vracejí kolekce, existují dvě další metody, které v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazech často používáte. Metoda vrací hodnotu Single <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda vrací hodnotu Single <xref:System.Xml.Linq.XAttribute>. <xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 Pro mnoho účelů [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy poskytují nejúčinnější způsob, jak kontrolovat strom, extrahovat z něj data a transformovat ho. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]dotazy fungují na objektech, <xref:System.Collections.Generic.IEnumerable%601>které implementují [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , a <xref:System.Collections.Generic.IEnumerable%601> na <xref:System.Xml.Linq.XElement> osách vrací kolekce <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Xml.Linq.XAttribute> kolekce. Tyto kolekce budete potřebovat k provádění dotazů.  
  
 Kromě metod osy, které načítají kolekce prvků a atributů, existují metody osy, které umožňují iterovat ve stromové struktuře Skvělé podrobnosti. Například místo řešení prvků a atributů můžete pracovat s uzly stromu. Uzly jsou jemnějším stupněm členitosti než prvky a atributy. Při práci s uzly můžete prozkoumávat komentáře XML, textové uzly, instrukce pro zpracování a další. Tato funkce je důležitá, například pro někoho, kdo napisuje textový procesor a chce uložit dokumenty jako XML. Většina programátorů XML je však primárně dotčena prvky, atributy a jejich hodnotami.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pro načtení kolekce prvků  
 Následuje souhrn metod <xref:System.Xml.Linq.XElement> třídy (nebo jejích základních tříd), které zavoláte <xref:System.Xml.Linq.XElement> pro vrácení kolekce prvků.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Xml.Linq.XElement> z nadřazených prvků tohoto prvku. <xref:System.Collections.Generic.IEnumerable%601> Přetížení vrátí sadu nadřazených <xref:System.Xml.Linq.XElement> prvků, které mají zadanou <xref:System.Xml.Linq.XName>hodnotu <xref:System.Collections.Generic.IEnumerable%601> .|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Vrátí ze <xref:System.Xml.Linq.XElement> následníků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> od <xref:System.Xml.Linq.XElement> následníků, které mají zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Vrátí z <xref:System.Xml.Linq.XElement> podřízených prvků tohoto prvku. Přetížení vrátí <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> podřízených elementů, které mají zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Vrátí prvek <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které jsou zadány po tomto prvku. Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků za tímto prvkem, který má zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Xml.Linq.XElement> z prvků, které jsou zadány před tímto prvkem. <xref:System.Collections.Generic.IEnumerable%601> Přetížení vrátí prvek <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků před tímto prvkem, který má zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Xml.Linq.XElement> z tohoto prvku a jeho nadřazených prvků. <xref:System.Collections.Generic.IEnumerable%601> Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Xml.Linq.XElement> z tohoto prvku a jeho následníků. <xref:System.Collections.Generic.IEnumerable%601> Přetížení vrátí hodnotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> prvků, které mají zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pro načtení jednoho elementu  
 Následující metoda načte jeden podřízený <xref:System.Xml.Linq.XElement> objekt z objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Vrátí první podřízený <xref:System.Xml.Linq.XElement> objekt, který má zadanou <xref:System.Xml.Linq.XName>hodnotu.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pro načtení kolekce atributů  
 Následující metoda načte atributy z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Vrátí hodnotu <xref:System.Xml.Linq.XAttribute>zevšechatributů. <xref:System.Collections.Generic.IEnumerable%601>|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pro načtení jednoho atributu  
 Následující metoda načte jeden atribut z <xref:System.Xml.Linq.XElement> objektu.  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Vrátí, který má zadanou <xref:System.Xml.Linq.XName>hodnotu. <xref:System.Xml.Linq.XAttribute>|  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes.md)
