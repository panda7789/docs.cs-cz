---
title: Překlad externích prostředků
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
ms.openlocfilehash: 05cc41cef7da07581d4f0ec8e584858b913d1a80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710268"
---
# <a name="resolving-external-resources"></a>Překlad externích prostředků
Vlastnost **objekt XmlResolver** třídy **XmlDocument** je používána třídou **XmlDocument** k vyhledání prostředků, které nejsou vloženy do dat XML, jako jsou definice typu externího dokumentu (DTD), entity a schémata. Tyto položky se můžou nacházet v síti nebo na místním disku a dají se identifikovat pomocí identifikátoru URI (Uniform Resource Identifier). To umožňuje **XmlDocument** přeložit uzly **EntityReference** , které jsou k dispozici v dokumentu, a ověřit dokument v závislosti na externí specifikaci DTD nebo schématu.  
  
## <a name="fully-trusted-xmldocument"></a>Plně důvěryhodná XmlDocument  
 Vlastnost **objekt XmlResolver** má vliv na funkčnost metody **XmlDocument. Load** . Následující tabulka ukazuje, jak vlastnost **XmlDocument. objekt XmlResolver** funguje, když je objekt **XmlDocument** plně důvěryhodný. V následující tabulce jsou uvedeny metody **XmlDocument. Load** , když vstup do zátěže je **TextReader**, **String**, **Stream**nebo **URI**. Tato tabulka se nevztahuje na metodu **Load** , pokud je **XmlDocument** načten z objektu **XmlReader**.  
  
|Vlastnost objekt XmlResolver|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Vlastnost je nastavena na třídu **objekt XmlResolver** , která byla dříve vytvořena a má vlastnosti již nastavené uživatelem.|**XmlDocument** používá **objekt XmlResolver** , který je předaný k překladu názvů souborů, k překladu odkazů na externí prostředky, jako jsou DTD, entity a schémata.<br /><br /> **Objekt XmlResolver** se používá také při překladu externích prostředků, které jsou potřeba při přidávání nebo úpravách uzlů v **XmlDocument**.|**Objekt XmlResolver** , který je dán pro **XmlDocument** , je překladač, který se používá, když je potřeba umístit a vyřešit externí prostředky.|  
|Vlastnost je nastavena na **hodnotu null** (**Nothing** v Microsoft Visual Basic .NET).|Funkce, které vyžadují externí prostředek, nejsou podporovány, například vyhledání externích schémat nebo DTD. Ani externí entity nebudou vyřešeny a provádět funkce úprav, například vkládání uzlů entit, které vyžadují řešení, nejsou podporovány.|**XmlDocument** načte soubory jako anonymní a nepokusí se přeložit žádné jiné prostředky.|  
|Vlastnost není nastavena, ale je ponechána ve výchozím stavu.|**XmlUrlResolver** s přihlašovacími údaji s hodnotou null bude při úpravě názvů souborů, vyhledání externích definic DTD, entit a schémat a **použití přihlašovacích** údajů null **použita při překladu** uzlů.||  
  
 V následující tabulce je uvedena metoda **XmlDocument. Load** , když vstup do **zátěže** je **XmlReader a třída** **XmlDocument** je plně důvěryhodná.  
  
|Vlastnost objekt XmlResolver|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Třída **objekt XmlResolver** , kterou používá **XmlDocument** , je stejná jako třída, kterou používá **třída XmlReader**.|**XmlDocument** používá **objekt XmlResolver** , který byl přiřazen objektu **XmlReader**.<br /><br /> Vlastnost **XmlDocument. překladač** nelze nastavit bez ohledu na úroveň vztahu důvěryhodnosti **XmlDocument** , protože načítá **objekt XmlResolver** z objektu **XmlReader**. Nemůžete se pokusit přepsat nastavení **objekt XmlResolver** objektů **XmlReader**nastavením vlastnosti **objekt XmlResolver** pro **XmlDocument**.|Objektem XmlReader může být **Třída** **XmlTextReader**, **XmlValidatingReader**nebo uživatelsky napsaného čtecího modulu. Pokud čtečka podporuje řešení entit, vyřeší se externí entity. Pokud čtecí modul předaný nepodporuje odkazy na entity, nevyřešily se odkazy na entity.|  
  
## <a name="semi-trusted-xmldocument"></a>Částečně důvěryhodná XmlDocument  
 Následující tabulka ukazuje, jak vlastnost **XmlDocument. objekt XmlResolver** funguje, když je objekt částečně důvěryhodný. Tato tabulka platí pro metody **XmlDocument. Load** při vstupu do zátěže je **TextReader**, **String**, **Stream**nebo **URI**. Tato tabulka se nevztahuje na metodu **Load** , pokud je **XmlDocument** načten z objektu **XmlReader**.  
  
|Vlastnost objekt XmlResolver|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|V částečně důvěryhodném scénáři nelze vlastnost **objekt XmlResolver** nastavit na jinou hodnotu než null.|**XmlUrlResolver** s přihlašovacími údaji s **hodnotou null** bude při úpravě názvů souborů, vyhledání externích definic DTD, entit a schémat a **použití přihlašovacích** údajů null **použita při překladu** uzlů.|Toto chování se shoduje s chováním, když není nastavena vlastnost **objekt XmlResolver** , ale zůstala ve výchozím stavu.<br /><br /> **XmlDocument** používá anonymní oprávnění pro všechny akce.|  
|Vlastnost je nastavena na **hodnotu null** (**Nothing** v Microsoft Visual Basic .NET).|Nejsou podporovány žádné funkce, které vyžadují externí prostředek, například vyhledání externího schématu nebo DTD. Ani externí entity nebudou vyřešeny a provádění funkcí úprav, jako je například vkládání uzlů entit, které vyžadují řešení, se nepodporuje.|Pokud má vlastnost **hodnotu null**, chování je stejné bez ohledu na to, jestli je **XmlDocument** plně důvěryhodný nebo částečně důvěryhodný.|  
|Vlastnost není nastavena, ale je ponechána ve výchozím stavu.|**XmlUrlResolver** s přihlašovacími údaji s **hodnotou null** bude při úpravě názvů souborů, vyhledání externích definic DTD, entit a schémat a **použití přihlašovacích** údajů null **použita při překladu** uzlů.|**XmlDocument** používá anonymní oprávnění pro všechny akce.|  
  
 Tato tabulka platí pro metodu **XmlDocument. Load** v případě, že vstup do **zatížení** je **třída XmlReader**a prvek **XmlDocument** je částečně důvěryhodný.  
  
|Vlastnost objekt XmlResolver|Funkce|Poznámky|  
|--------------------------|--------------|-----------|  
|Třída **objekt XmlResolver** používaná třídou **XmlDocument** je stejná jako ta, kterou používá objekt **XmlReader**.|**XmlDocument** používá **objekt XmlResolver** , který byl přiřazen objektu **XmlReader**.<br /><br /> Vlastnost **XmlDocument. překladač** nelze nastavit bez ohledu na úroveň vztahu důvěryhodnosti **XmlDocument** , protože načítá **objekt XmlResolver** z objektu **XmlReader**. Nemůžete se pokusit přepsat nastavení **objekt XmlResolver** objektů **XmlReader** nastavením vlastnosti **objekt XmlResolver** pro **XmlDocument**.|Objektem XmlReader může být **Třída** **XmlTextReader**, <xref:System.Xml.XmlReader>ověřování nebo uživatelsky napsané čtecí zařízení. Pokud čtečka podporuje řešení entit, vyřeší se externí entity. Pokud čtenář předaný není podporován odkazy na entity, odkazy na entity nejsou vyřešeny.|  
  
 Nastavení objekt XmlResolver tak, aby obsahovalo správné přihlašovací údaje, umožňuje přístup k externím prostředkům.  
  
> [!NOTE]
> Neexistuje žádný způsob, jak načíst vlastnost **objekt XmlResolver** . To pomáhá zabránit uživateli v použití **objekt XmlResolver** , u kterého byla nastavena pověření. Kromě toho, pokud **XmlTextReader** je použita položka <xref:System.Xml.XmlReader> XmlTextReader nebo Valid pro načtení souboru **XmlDocument** a prvek **XmlDocument** obsahuje překladač, který byl nastaven, překladače z těchto čtecích zařízení nejsou uloženy v mezipaměti **XmlDocument** po fázi **zatížení** , protože to také představuje bezpečnostní riziko.  
  
 Další informace naleznete v části poznámky na <xref:System.Xml.XmlResolver> referenční stránce.  
  
## <a name="see-also"></a>Viz také

- [model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
