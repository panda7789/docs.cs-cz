---
title: Platný obsah XElement a XDocument Objects3
description: Přečtěte si o platných argumentech, které lze předat konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302253"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Platný obsah objektů XElement a XDocument
Toto téma popisuje platné argumenty, které mohou být předány konstruktorům a metodám, které slouží k přidání obsahu do prvků a dokumentů.  
  
## <a name="valid-content"></a>Platný obsah  
 Dotazy jsou často vyhodnoceny jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> . Můžete předat kolekce <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> objektů nebo do <xref:System.Xml.Linq.XElement> konstruktoru. Proto je vhodné předat výsledky dotazu jako obsah do metod a konstruktorů, které slouží k naplnění stromů XML.  
  
 Při přidávání jednoduchého obsahu je možné do této metody předat různé typy. Mezi platné typy patří následující:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Jakýkoli typ, který implementuje `Object.ToString` .  
  
- Jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> .  
  
 Při přidávání komplexního obsahu je možné do této metody předat různé typy:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Jakýkoli typ, který implementuje<xref:System.Collections.Generic.IEnumerable%601>  
  
 Pokud objekt implementuje, je vyhodnocena <xref:System.Collections.Generic.IEnumerable%601> kolekce v objektu a jsou přidány všechny položky v kolekci. Pokud kolekce obsahuje <xref:System.Xml.Linq.XNode> objekty nebo <xref:System.Xml.Linq.XAttribute> , každá položka v kolekci se přidá samostatně. Pokud kolekce obsahuje text (nebo objekty, které jsou převedeny na text), je text v kolekci zřetězen a přidán jako jediný textový uzel.  
  
 Pokud je obsah `null` , nic se nepřidá. Při předávání položek kolekce v kolekci může být `null` . `null`Položka v kolekci nemá žádný vliv na strom.  
  
 Přidaný atribut musí mít jedinečný název v rámci jeho nadřazeného elementu.  
  
 Pokud při <xref:System.Xml.Linq.XNode> přidávání <xref:System.Xml.Linq.XAttribute> objektů nebo objektů není k dispozici žádný nadřazený obsah, jsou objekty jednoduše připojeny ke stromu XML. Pokud je nový obsah již nadřazený a je součástí jiného stromu XML, bude nový obsah naklonován a nově Klonovaný obsah bude připojen ke stromu XML.  
  
## <a name="valid-content-for-documents"></a>Platný obsah pro dokumenty  
 Do dokumentu nelze přidat atributy a jednoduchý obsah.  
  
 Neexistuje mnoho scénářů, které vyžadují, abyste vytvořili <xref:System.Xml.Linq.XDocument> . Místo toho můžete obvykle vytvořit stromy XML s <xref:System.Xml.Linq.XElement> kořenovým uzlem. Pokud nemáte konkrétní požadavek na vytvoření dokumentu (například proto, že potřebujete vytvořit instrukce a komentáře pro zpracování na nejvyšší úrovni nebo potřebujete podporovat typy dokumentů), je často pohodlnější použít <xref:System.Xml.Linq.XElement> jako kořenový uzel.  
  
 Platný obsah dokumentu zahrnuje následující:  
  
- Nula nebo jeden <xref:System.Xml.Linq.XDocumentType> objekt. Typy dokumentů musí předcházet elementu.  
  
- Nula nebo jeden prvek.  
  
- Nula nebo více komentářů  
  
- Nula nebo více instrukcí pro zpracování.  
  
- Nula nebo více textových uzlů, které obsahují pouze prázdné znaky.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory a funkce umožňující přidání obsahu  
 Následující metody umožňují přidat podřízený obsah do <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> :  
  
|Metoda|Popis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Vytvoří <xref:System.Xml.Linq.XDocument> .|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Přidá na konec podřízeného obsahu <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> .|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Přidá obsah za <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Přidá obsah před <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Přidá obsah na začátek podřízeného obsahu <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Nahradí veškerý obsah (podřízené uzly a atributy) typu <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Nahradí atributy <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Nahradí podřízené uzly novým obsahem.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Nahradí uzel novým obsahem.|  
  
## <a name="see-also"></a>Viz také:

- [Vytváření stromů XML (C#)](./linq-to-xml-overview.md)
