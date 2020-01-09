---
title: Úprava uzlů, obsahu a hodnot v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
ms.openlocfilehash: 4a53ba4fe16a3653b1be380da49e6b75cb347a28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710671"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Úprava uzlů, obsahu a hodnot v dokumentu XML
Existuje mnoho způsobů, jak můžete změnit uzly a obsah v dokumentu. Můžeš:  
  
- Změňte hodnotu uzlů pomocí vlastnosti <xref:System.Xml.XmlNode.Value%2A>.  
  
- Upravte celou sadu uzlů nahrazením uzlů novými uzly. To se provádí pomocí vlastnosti <xref:System.Xml.XmlNode.InnerXml%2A>.  
  
- Nahraďte stávající uzly novými uzly pomocí metody <xref:System.Xml.XmlNode.RemoveChild%2A>.  
  
- Přidejte další znaky do uzlů, které dědí z třídy <xref:System.Xml.XmlCharacterData> pomocí metod <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>nebo <xref:System.Xml.XmlCharacterData.ReplaceData%2A>.  
  
- Upravte obsah tak, že odeberete rozsah znaků pomocí metody <xref:System.Xml.XmlCharacterData.DeleteData%2A> u typů uzlů, které dědí z <xref:System.Xml.XmlCharacterData>.  
  
 Jednoduchá technika pro změnu hodnoty uzlu je použití `node.Value = "new value";`. V následující tabulce jsou uvedeny typy uzlů, na kterých tento jediný řádek kódu funguje, a přesně jaká data pro daný typ uzlu jsou změněna.  
  
|Typ uzlu|Data změněna|  
|---------------|------------------|  
|Atribut|Hodnota atributu.|  
|CDATASection|Obsah CDATASection|  
|Komentář|Obsah komentáře|  
|ProcessingInstruction|Obsah s výjimkou cíle.|  
|Text|Obsah textu.|  
|XmlDeclaration|Obsah deklarace, kromě `<?xml` a značek `?>`|  
|Typy|Hodnota prázdného místa. Hodnotu můžete nastavit jako jeden ze čtyř rozpoznaných prázdných znaků XML: mezera, tabulátor, CR nebo LF.|  
|SignificantWhitespace|Hodnota významného prázdného místa. Hodnotu můžete nastavit jako jeden ze čtyř rozpoznaných prázdných znaků XML: mezera, tabulátor, CR nebo LF.|  
  
 Žádný typ uzlu, který není uveden v tabulce, není platný typ uzlu pro nastavení hodnoty. Nastavení hodnoty na jiném typu uzlu vyvolá <xref:System.InvalidOperationException>.  
  
 Vlastnost <xref:System.Xml.XmlNode.InnerXml%2A> změní označení podřízených uzlů pro aktuální uzel. Nastavení této vlastnosti nahradí podřízené uzly analyzovaným obsahem daného řetězce. Analýza je provedena v aktuálním kontextu oboru názvů. Kromě toho <xref:System.Xml.XmlNode.InnerXml%2A> odebere nadbytečné deklarace oboru názvů. V důsledku toho mnoho operací vyjmutí a vložení nezvětšuje velikost dokumentu pomocí redundantních deklarací oboru názvů. Příklad kódu znázorňující účinek oborů názvů v operaci <xref:System.Xml.XmlNode.InnerXml%2A> najdete v tématu vlastnost <xref:System.Xml.XmlDocument.InnerXml%2A>.  
  
 Při použití metod <xref:System.Xml.XmlCharacterData.ReplaceData%2A> a <xref:System.Xml.XmlNode.RemoveChild%2A> vrátí metody nahrazený nebo odebraný uzel. Tento uzel lze následně znovu vložit do jiného v XML model DOM (Document Object Model) (DOM). Metoda <xref:System.Xml.XmlCharacterData.ReplaceData%2A> provádí dvě ověřovací kontroly na uzlu, který je vložen do dokumentu. První ověření zajistí, že se uzel stane podřízenou položkou uzlu, který může mít podřízené uzly svého typu. Druhá kontrolu zajistí, že vložený uzel není nadřazeným uzlem uzlu, který se stává podřízenou položkou. Porušení některé z těchto podmínek vyvolá <xref:System.InvalidOperationException>.  
  
 Přidání nebo odebrání podřízeného objektu jen pro čtení z uzlu, který lze upravovat, je neplatné. Pokusy o změnu samotného uzlu, který je jen pro čtení, ale vyvolá <xref:System.InvalidOperationException>. Příkladem je změna podřízených objektů uzlu <xref:System.Xml.XmlEntityReference>. Podřízené objekty jsou jen pro čtení a nelze je upravit. Jakékoli pokusy o jejich změnu vyvolá <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
