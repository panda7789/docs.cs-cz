---
title: Úprava uzlů, obsahu a hodnot v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: f544b7d8472285095af9a71b1c24f94f61f93bc6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288820"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Úprava uzlů, obsahu a hodnot v dokumentu XML
Existuje mnoho způsobů, jak můžete změnit uzly a obsah v dokumentu. Další možnosti:  
  
- Změňte hodnotu uzlů pomocí <xref:System.Xml.XmlNode.Value%2A> Vlastnosti.  
  
- Upravte celou sadu uzlů nahrazením uzlů novými uzly. To se provádí pomocí <xref:System.Xml.XmlNode.InnerXml%2A> Vlastnosti.  
  
- Nahraďte existující uzly novými uzly pomocí <xref:System.Xml.XmlNode.RemoveChild%2A> metody.  
  
- Přidejte další znaky do uzlů, které dědí z <xref:System.Xml.XmlCharacterData> třídy pomocí <xref:System.Xml.XmlCharacterData.AppendData%2A> metod, <xref:System.Xml.XmlCharacterData.InsertData%2A> nebo <xref:System.Xml.XmlCharacterData.ReplaceData%2A> .  
  
- Upravte obsah tak, že odeberete rozsah znaků pomocí <xref:System.Xml.XmlCharacterData.DeleteData%2A> metody na typech uzlů, které dědí z <xref:System.Xml.XmlCharacterData> .  
  
 Jednoduchá technika pro změnu hodnoty uzlu je použití `node.Value = "new value";` . V následující tabulce jsou uvedeny typy uzlů, na kterých tento jediný řádek kódu funguje, a přesně jaká data pro daný typ uzlu jsou změněna.  
  
|Typ uzlu|Data změněna|  
|---------------|------------------|  
|Atribut|Hodnota atributu|  
|CDATASection|Obsah CDATASection|  
|Komentář|Obsah komentáře|  
|ProcessingInstruction|Obsah s výjimkou cíle.|  
|Text|Obsah textu|  
|XmlDeclaration|Obsah deklarace, kromě `<?xml` `?>` značek a.|  
|Prázdné znaky|Hodnota prázdného místa. Hodnotu můžete nastavit jako jeden ze čtyř rozpoznaných prázdných znaků XML: mezera, tabulátor, CR nebo LF.|  
|SignificantWhitespace|Hodnota významného prázdného místa. Hodnotu můžete nastavit jako jeden ze čtyř rozpoznaných prázdných znaků XML: mezera, tabulátor, CR nebo LF.|  
  
 Žádný typ uzlu, který není uveden v tabulce, není platný typ uzlu pro nastavení hodnoty. Nastavení hodnoty na jiném typu uzlu vyvolá <xref:System.InvalidOperationException> .  
  
 <xref:System.Xml.XmlNode.InnerXml%2A>Vlastnost změní označení podřízených uzlů pro aktuální uzel. Nastavení této vlastnosti nahradí podřízené uzly analyzovaným obsahem daného řetězce. Analýza je provedena v aktuálním kontextu oboru názvů. Kromě toho <xref:System.Xml.XmlNode.InnerXml%2A> Odebere nadbytečné deklarace oboru názvů. V důsledku toho mnoho operací vyjmutí a vložení nezvětšuje velikost dokumentu pomocí redundantních deklarací oboru názvů. Příklad kódu znázorňující vliv oborů názvů na <xref:System.Xml.XmlNode.InnerXml%2A> operaci naleznete v tématu <xref:System.Xml.XmlDocument.InnerXml%2A> Property.  
  
 Při použití <xref:System.Xml.XmlCharacterData.ReplaceData%2A> metod a <xref:System.Xml.XmlNode.RemoveChild%2A> vrátí metody nahrazený nebo odebraný uzel. Tento uzel lze následně znovu vložit do jiného v XML model DOM (Document Object Model) (DOM). <xref:System.Xml.XmlCharacterData.ReplaceData%2A>Metoda provádí dvě ověřovací kontroly na uzlu, který je vložen do dokumentu. První ověření zajistí, že se uzel stane podřízenou položkou uzlu, který může mít podřízené uzly svého typu. Druhá kontrolu zajistí, že vložený uzel není nadřazeným uzlem uzlu, který se stává podřízenou položkou. Porušení některé z těchto podmínek vyvolá <xref:System.InvalidOperationException> .  
  
 Přidání nebo odebrání podřízeného objektu jen pro čtení z uzlu, který lze upravovat, je neplatné. Pokusy o změnu samotného uzlu, který je jen pro čtení, ale vyvolá <xref:System.InvalidOperationException> . Příkladem je úprava podřízených objektů <xref:System.Xml.XmlEntityReference> uzlu. Podřízené objekty jsou jen pro čtení a nelze je upravit. Libovolný pokus o jeho úpravu vyvolá <xref:System.InvalidOperationException> .  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](xml-document-object-model-dom.md)
