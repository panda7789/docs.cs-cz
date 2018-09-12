---
title: Překlad externích prostředků
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef31d101769dca00f5cff545c72b3afbd59bc638
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509983"
---
# <a name="resolving-external-resources"></a>Překlad externích prostředků
**Objekt XmlResolver** vlastnost **XmlDocument** používá **třídou XMLDocument nastavenou na** třídy najít prostředky, které nejsou vložené v datech XML, jako je například typ externího dokumentu definice (DTD), entit a schémata. Tyto položky mohou být umístěny v síti nebo na místním disku a identifikovat podle identifikátor URI (Uniform Resource). Díky tomu **XmlDocument** vyřešit **EntityReference** uzlů, které jsou k dispozici v dokumentu a ověřit dokument podle externí DTD nebo schématu.  
  
## <a name="fully-trusted-xmldocument"></a>Plně důvěryhodné XmlDocument  
 **Objekt XmlResolver** vlastnost má vliv na funkci **XmlDocument.Load** metody. V tabulce níže ukazuje jak **XmlDocument.XmlResolver** vlastnost funguje, když **XmlDocument** objektu je plně důvěryhodné. Následující tabulka ukazuje **XmlDocument.Load** metody, když je vstup pro zatížení **TextReader**, **řetězec**, **Stream**, nebo  **Identifikátor URI**. Tato tabulka se nedá použít u **zatížení** metoda Pokud **třídou XMLDocument nastavenou na** je načteno z **XmlReader**.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Je nastavena na **objekt XmlResolver** třídu, která byla dříve vytvořena a má vlastnosti již nastaven na něm uživatel.|**XmlDocument** používá **objekt XmlResolver** , která je přidělena přeložit názvy souborů, chcete-li vyřešit odkazy na externí prostředky, jako je specifikace DTD, entit a schémata.<br /><br /> **Objekt XmlResolver** se také používá při překlad externích prostředků, které jsou potřeba při přidávání nebo úpravách uzly v **XmlDocument**.|**Objekt XmlResolver** věnovat **XmlDocument** je překladače, který se používá při každém externím prostředkům potřeba nachází a vyřešit.|  
|Je nastavena na **null** (**nic** v aplikaci Microsoft Visual Basic .NET).|Funkce, které vyžadují externího prostředku nejsou podporovány, jako je například hledání externí schéma nebo DTD. Ani externí entity bude vyřešen a provádí úpravy funkce, jako je například vkládání uzlů entity, které vyžadují řešení, se nepodporují.|**XmlDocument** načte soubory pod označením anonymní a nebude pokoušet o vyřešit všechny další prostředky.|  
|Vlastnost není nastavena, ale zbývá ve svém výchozím stavu.|**XmlUrlResolver** s hodnotou NULL pověření vytvořena instance, který se používá **XmlDocument** při překládání názvů souboru, vyhledávání externí specifikace DTD, entit a schémata, a **null** přihlašovací údaje se používají při úpravách uzly.||  
  
 Následující tabulka ukazuje **XmlDocument.Load** – metoda při vstupu do **zatížení** je **XmlReader** a **třídou XMLDocument nastavenou na** je plně důvěryhodné.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|**Objekt XmlResolver** třídy používané **XmlDocument** je stejnou třídou, která je používána ve **XmlReader**.|**XmlDocument** používá **objekt XmlResolver** , který byl přiřazen **XmlReader**.<br /><br /> **XmlDocument.Resolver** nemůže být vlastnost nastavena, bez ohledu na to **XmlDocument** úroveň, důvěryhodnosti, protože je stále **objekt XmlResolver** z  **Objekt XmlReader**. Pokusíte přepsat nastavení **XmlReaders**" **objekt XmlResolver** nastavením **objekt XmlResolver** vlastnost **XmlDocument**.|**XmlReader** může být **XmlTextReader**, **objekt XmlValidatingReader**, nebo čtečku zapisovat vlastní. Pokud čtení byl použit podporuje entity řešení, jsou vyřešeny externí entity. Pokud čtečka nepodporuje odkazy na entity, pak nejsou přeložit odkazy na entity.|  
  
## <a name="semi-trusted-xmldocument"></a>Částečně důvěryhodné XmlDocument  
 Následující tabulka ukazuje jak **XmlDocument.XmlResolver** vlastnost funguje, když je objekt částečně důvěryhodné. Tato tabulka platí pro **XmlDocument.Load** metody, když je vstup pro zatížení **TextReader**, **řetězec**, **Stream**, nebo  **Identifikátor URI**. Tato tabulka se nedá použít u **zatížení** metoda Pokud **třídou XMLDocument nastavenou na** je načteno z **XmlReader**.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|V částečně důvěryhodné scénáři **objekt XmlResolver** vlastnost nemůže být nastavena na jinou hodnotu než null.|**XmlUrlResolver** s **null** pověření vytvořena instance, který se používá **XmlDocument** při překládání názvů souboru, vyhledávání externí specifikace DTD, entity, a schémata, a **null** přihlašovací údaje se používají při úpravách uzly.|Toto chování je stejné jako chování při **objekt XmlResolver** vlastnost není nastavena, ale zbývá ve svém výchozím stavu.<br /><br /> **XmlDocument** používá anonymní oprávnění pro všechny akce.|  
|Je nastavena na **null** (**nic** v aplikaci Microsoft Visual Basic .NET).|Žádné funkce, které vyžadují externího prostředku jsou podporovány, jako je například vyhledávání externí schématu nebo souboru DTD. Ani externí entity bude vyřešen a provádí úpravy funkce jako je například vkládání uzlů entity, které vyžadují řešení, nejsou podporovány.|Pokud je vlastnost **null**, chování je stejný bez ohledu na to, když **XmlDocument** plně důvěryhodný nebo je částečně důvěryhodné.|  
|Vlastnost není nastavena, ale zbývá ve svém výchozím stavu.|**XmlUrlResolver** s **null** pověření vytvořena instance, který se používá **XmlDocument** při překládání názvů souboru, vyhledávání externí specifikace DTD, entity, a schémata, a **null** přihlašovací údaje se používají při úpravách uzly.|**XmlDocument** používá anonymní oprávnění pro všechny akce.|  
  
 Tato tabulka platí pro **XmlDocument.Load** – metoda při vstupu do **zatížení** je **XmlReader**a **třídou XMLDocument nastavenou na** je částečně důvěryhodné.  
  
|Objekt XmlResolver vlastnost|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|**Objekt XmlResolver** třídy používané **XmlDocument** je stejná jako ta, která je používána ve **XmlReader**.|**XmlDocument** používá **objekt XmlResolver** , který byl přiřazen **XmlReader**.<br /><br /> **XmlDocument.Resolver** nemůže být vlastnost nastavena, bez ohledu na to **XmlDocument** úroveň, důvěryhodnosti, protože je stále **objekt XmlResolver** z  **Objekt XmlReader**. Pokusíte přepsat nastavení **XmlReaders** **objekt XmlResolver** nastavením **objekt XmlResolver** vlastnost **XmlDocument**.|**XmlReader** může být **XmlTextReader**, ověřování <xref:System.Xml.XmlReader>, nebo čtečku zapisovat vlastní. Pokud čtení byl použit podporuje entity řešení, jsou vyřešeny externí entity. Pokud čtečka předaný nepodporuje odkazy na entity, nejsou přeložit odkazy na entity.|  
  
 Nastavení objekt XmlResolver tak, aby obsahovala správné přihlašovací údaje umožní přístup k externím prostředkům.  
  
> [!NOTE]
>  Neexistuje žádný způsob, jak načíst **objekt XmlResolver** vlastnost. To pomáhá zabránit uživateli v opakovaném použití **objekt XmlResolver** na jaké přihlašovací údaje jsou nastavené. Také pokud **XmlTextReader** nebo ověřování <xref:System.Xml.XmlReader> slouží k načtení **XmlDocument** a **třídou XMLDocument nastavenou na** má překladače byla nastavena, překladače z neukládá do mezipaměti tyto čtenáři **XmlDocument** po **zatížení** fáze, protože to také představuje bezpečnostní riziko.  
  
 Další informace najdete v části poznámky <xref:System.Xml.XmlResolver> referenční stránce.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
