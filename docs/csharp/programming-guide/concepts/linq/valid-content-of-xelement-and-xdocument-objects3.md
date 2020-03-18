---
title: Platný obsah objektů XElement a XDocument3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590935"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Platný obsah objektů XElement a XDocument
Toto téma popisuje platné argumenty, které mohou být předány konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.  
  
## <a name="valid-content"></a>Platný obsah  
 Dotazy <xref:System.Collections.Generic.IEnumerable%601> často vyhodnocují do nebo <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Konstruktoru <xref:System.Xml.Linq.XElement> můžete předat <xref:System.Xml.Linq.XAttribute> kolekce <xref:System.Xml.Linq.XElement> nebo objekty. Proto je vhodné předat výsledky dotazu jako obsah do metod a konstruktorů, které používáte k naplnění stromů XML.  
  
 Při přidávání jednoduchého obsahu mohou být této metodě předány různé typy. Mezi platné typy patří následující:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Libovolný typ, `Object.ToString`který implementuje .  
  
- Libovolný typ, <xref:System.Collections.Generic.IEnumerable%601>který implementuje .  
  
 Při přidávání komplexního obsahu mohou být této metodě předány různé typy:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Libovolný typ, který implementuje<xref:System.Collections.Generic.IEnumerable%601>  
  
 Pokud objekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekce v objektu je výčtu a jsou přidány všechny položky v kolekci. Pokud kolekce <xref:System.Xml.Linq.XNode> obsahuje <xref:System.Xml.Linq.XAttribute> nebo objekty, každá položka v kolekci je přidán samostatně. Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), text v kolekci je zřetězena a přidána jako jeden textový uzel.  
  
 Pokud je `null`obsah , nic není přidáno. Při předávání položek kolekce v `null`kolekci může být . Položka `null` v kolekci nemá žádný vliv na strom.  
  
 Přidaný atribut musí mít jedinečný název v rámci obsahujícího prvku.  
  
 Při <xref:System.Xml.Linq.XNode> přidávání nebo <xref:System.Xml.Linq.XAttribute> objekty, pokud nový obsah nemá nadřazený, pak objekty jsou jednoduše připojeny ke stromu XML. Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, je nový obsah klonován a nově klonovaný obsah je připojen ke stromu XML.  
  
## <a name="valid-content-for-documents"></a>Platný obsah pro dokumenty  
 Atributy a jednoduchý obsah nelze přidat do dokumentu.  
  
 Není mnoho scénářů, které vyžadují <xref:System.Xml.Linq.XDocument>vytvoření . Místo toho můžete obvykle vytvořit stromy <xref:System.Xml.Linq.XElement> XML s kořenovým uzlem. Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto, že musíte vytvořit pokyny pro zpracování a komentáře na nejvyšší úrovni <xref:System.Xml.Linq.XElement> nebo musíte podporovat typy dokumentů), je často vhodnější použít jako kořenový uzel.  
  
 Platný obsah dokumentu zahrnuje následující:  
  
- Nula <xref:System.Xml.Linq.XDocumentType> nebo jeden objekt. Typy dokumentů musí být před elementem.  
  
- Nula nebo jeden prvek.  
  
- Nula nebo více komentářů.  
  
- Nula nebo více pokynů pro zpracování.  
  
- Nula nebo více uzly textu, které obsahují pouze prázdné znaky.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory a funkce, které umožňují přidávání obsahu  
 Následující metody umožňují přidat podřízený <xref:System.Xml.Linq.XElement> obsah <xref:System.Xml.Linq.XDocument>do aplikace nebo :  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá na konec podřízeného <xref:System.Xml.Linq.XElement> obsahu <xref:System.Xml.Linq.XDocument>nebo .|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah <xref:System.Xml.Linq.XNode>za .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah <xref:System.Xml.Linq.XNode>před .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátku podřízeného obsahu . <xref:System.Xml.Linq.XContainer>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Nahradí veškerý obsah (podřízené uzly <xref:System.Xml.Linq.XElement>a atributy) .|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Nahradí atributy . <xref:System.Xml.Linq.XElement>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Nahradí podřízené uzly novým obsahem.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Nahradí uzel novým obsahem.|  
  
## <a name="see-also"></a>Viz také

- [Vytváření stromů XML (C#)](./linq-to-xml-overview.md)
