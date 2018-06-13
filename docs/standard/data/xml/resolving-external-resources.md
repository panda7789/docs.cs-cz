---
title: Řešení externí zdroje
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1c56d69724212b9d1cd6a24204a12460071633f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577085"
---
# <a name="resolving-external-resources"></a>Řešení externí zdroje
**Objekt XmlResolver** vlastnost **třídou XMLDocument nastavenou na** je používán **třídou XMLDocument nastavenou na** třída najít prostředky, které nejsou vnořené v datech XML, jako je například externí dokument – typ definice (specifikace DTD), entit a schémat. Tyto položky může být umístěn v síti nebo na místní disk a identifikovat pomocí identifikátor URI (Uniform Resource). To umožňuje **třídou XMLDocument nastavenou na** vyřešit **EntityReference** uzlů, které jsou k dispozici v dokumentu a ověření dokumentu podle externí DTD nebo schéma.  
  
## <a name="fully-trusted-xmldocument"></a>Třídou XMLDocument nastavenou na plně důvěryhodná  
 **Objekt XmlResolver** vlastnost má vliv na funkci **XmlDocument.Load** metoda. V tabulce níže znázorňuje jak **XmlDocument.XmlResolver** vlastnost funguje, když **třídou XMLDocument nastavenou na** objektu je plně důvěryhodný. Následující tabulce je zobrazena **XmlDocument.Load** metody při vstupu do zatížení **TextReader**, **řetězec**, **datového proudu**, nebo  **Identifikátor URI**. Tato tabulka se nevztahuje **zatížení** metoda Pokud **třídou XMLDocument nastavenou na** je načíst z **XmlReader**.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Je nastavena na **objekt XmlResolver** třídu, která byla dříve vytvořena a již nastavena na něm uživatelem.|**Třídou XMLDocument nastavenou na** používá **objekt XmlResolver** , je zadána přeložit názvy souborů, odkazy na externím prostředkům, jako je specifikace DTD, entit a schémat.<br /><br /> **Objekt XmlResolver** se také používá při rozpoznávání externím prostředkům, které jsou potřeba při přidávání nebo úpravě uzly v **třídou XMLDocument nastavenou na**.|**Objekt XmlResolver** zadané **třídou XMLDocument nastavenou na** je překladač, který se používá při každém externí prostředky je nutné být umístěn a vyřešit.|  
|Je nastavena na **null** (**nic** v aplikaci Microsoft Visual Basic .NET).|Funkce, které vyžadují externí prostředek nepodporuje, jako je nalezení externí schéma nebo souboru DTD protokolu. Ani externí entity bude vyřešen a provádění úpravy funkce, jako je například vložení entity uzly, které vyžadují řešení, nejsou podporovány.|**Třídou XMLDocument nastavenou na** zatížení soubory jako anonymní a nebude pokoušet o vyřešit jiné prostředky.|  
|Vlastnost není nastavená, ale zbývající ve svém výchozím stavu.|**XmlUrlResolver** s hodnotou NULL přihlašovací údaje vytvořit instance, který se používá **třídou XMLDocument nastavenou na** při překladu názvů souborů, umísťování externí specifikace DTD, entit a schémat, a **null** přihlašovací údaje se používají při úpravě uzly.||  
  
 Následující tabulce je zobrazena **XmlDocument.Load** metoda při vstup **zatížení** je **XmlReader** a **třídou XMLDocument nastavenou na** je plně důvěryhodný.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|**Objekt XmlResolver** třídy používané **třídou XMLDocument nastavenou na** je stejnou třídou používán **XmlReader**.|**Třídou XMLDocument nastavenou na** používá **objekt XmlResolver** který byl přiřazen **XmlReader**.<br /><br /> **XmlDocument.Resolver** vlastnost nemůže být nastaveno, bez ohledu na to **třídou XMLDocument nastavenou na** úroveň, důvěryhodnosti, protože je získávání **objekt XmlResolver** z  **XmlReader**. Pokusíte přepsat nastavení **XmlReaders**' **objekt XmlResolver** nastavením **objekt XmlResolver** vlastnost **třídou XMLDocument nastavenou na**.|**XmlReader** může být **XmlTextReader**, **třídy XmlValidatingReader**, nebo vlastního čtečka čipových karet. Pokud čtečka používá podporuje entity řešení, se přeloží externí entity. Pokud čtečka předány nepodporuje odkazy na entity, pak entity, které nejsou odkazy vyřešit.|  
  
## <a name="semi-trusted-xmldocument"></a>Částečně důvěryhodné třídou XMLDocument nastavenou na  
 Následující tabulka ilustruje jak **XmlDocument.XmlResolver** vlastnost funguje, když je objekt polovičním důvěryhodný. Tato tabulka platí pro **XmlDocument.Load** metody při vstupu do zatížení **TextReader**, **řetězec**, **datového proudu**, nebo  **Identifikátor URI**. Tato tabulka se nevztahuje **zatížení** metoda Pokud **třídou XMLDocument nastavenou na** je načíst z **XmlReader**.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Ve scénáři, polovičním důvěryhodný **objekt XmlResolver** vlastnost nelze nastavit na jakoukoli jinou hodnotu než null.|**XmlUrlResolver** s **null** přihlašovací údaje vytvořit instance, který se používá **třídou XMLDocument nastavenou na** při překladu názvů souborů, vyhledání externí specifikace DTD, entity, a schémata a **null** přihlašovací údaje se používají při úpravě uzly.|Toto chování je stejné jako chování při **objekt XmlResolver** není nastavena vlastnost, ale zbývající ve svém výchozím stavu.<br /><br /> **Třídou XMLDocument nastavenou na** používá anonymní oprávnění pro všechny akce.|  
|Je nastavena na **null** (**nic** v aplikaci Microsoft Visual Basic .NET).|Žádné funkce, které vyžadují externí prostředek jsou podporovány, jako je například vyhledávání na externí schématu nebo souboru DTD protokolu. Ani externí entity bude vyřešen a provádění úpravy funkce jako je například vložení entity uzly, které vyžadují řešení, nejsou podporovány.|Pokud je vlastnost **null**, toto chování je stejné bez ohledu na to pokud **třídou XMLDocument nastavenou na** je plně důvěryhodné nebo částečně důvěryhodné.|  
|Vlastnost není nastavená, ale zbývající ve svém výchozím stavu.|**XmlUrlResolver** s **null** přihlašovací údaje vytvořit instance, který se používá **třídou XMLDocument nastavenou na** při překladu názvů souborů, vyhledání externí specifikace DTD, entity, a schémata a **null** přihlašovací údaje se používají při úpravě uzly.|**Třídou XMLDocument nastavenou na** používá anonymní oprávnění pro všechny akce.|  
  
 Tato tabulka platí pro **XmlDocument.Load** metoda při vstup **zatížení** je **XmlReader**a **třídou XMLDocument nastavenou na** je částečně důvěryhodné.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|**Objekt XmlResolver** třídy používané **třídou XMLDocument nastavenou na** je stejný jako ten, používá **XmlReader**.|**Třídou XMLDocument nastavenou na** používá **objekt XmlResolver** který byl přiřazen **XmlReader**.<br /><br /> **XmlDocument.Resolver** vlastnost nemůže být nastaveno, bez ohledu na to **třídou XMLDocument nastavenou na** úroveň, důvěryhodnosti, protože je získávání **objekt XmlResolver** z  **XmlReader**. Pokusíte přepsat nastavení **XmlReaders** **objekt XmlResolver** nastavením **objekt XmlResolver** vlastnost **třídou XMLDocument nastavenou na**.|**XmlReader** může být **XmlTextReader**, ověřuje <xref:System.Xml.XmlReader>, nebo vlastního čtečka čipových karet. Pokud čtečka používá podporuje entity řešení, se přeloží externí entity. Pokud čtečka předaná nepodporuje odkazy na entity, nejsou vyřešit odkazy na entity.|  
  
 Nastavení objekt XmlResolver tak, aby obsahovala správné přihlašovací údaje umožní přístup k externím prostředkům.  
  
> [!NOTE]
>  Neexistuje žádný způsob, jak načíst **objekt XmlResolver** vlastnost. To pomáhá zabránit uživateli v opakovaném použití **objekt XmlResolver** pověření, které byly nastaveny. Navíc pokud **XmlTextReader** nebo ověřování <xref:System.Xml.XmlReader> slouží k načtení **třídou XMLDocument nastavenou na** a **třídou XMLDocument nastavenou na** má překladač, která byla nastavena, překladače z Tyto čtečky se neukládají do mezipaměti pomocí **třídou XMLDocument nastavenou na** po **zatížení** fáze, protože to také představuje bezpečnostní riziko.  
  
 Další informace najdete v části poznámky <xref:System.Xml.XmlResolver> stránka s referencemi k.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
