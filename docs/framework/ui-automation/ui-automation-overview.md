---
title: Přehled automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: a306bfe4b794409f7f64359daee7e18d34826921
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441442"
---
# <a name="ui-automation-overview"></a>Přehled automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je nová architektura usnadnění pro Microsoft Windows, která je dostupná ve všech operačních systémech, které podporují [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje programový přístup k většině [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvků na ploše a umožňuje produktům pro usnadnění, jako jsou čtečky obrazovky, poskytovat informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] koncovým uživatelům a manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pomocí jiného než standardního vstupu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] také umožňuje automatickým testovacím skriptům pracovat s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] neumožňuje komunikaci mezi procesy spuštěnými různými uživateli prostřednictvím příkazu **Spustit jako** .  
  
 Klientské aplikace automatizace uživatelského rozhraní lze zapsat s jistotou, že budou fungovat na více architekturách. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core maskuje jakékoli rozdíly v rozhraních, které jsou základem různých částí [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Například vlastnost `Content` [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítko, vlastnost `Caption` tlačítka [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] a vlastnost `ALT` obrázku HTML je namapována na jedinou vlastnost, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>v zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
Automatizace uživatelského rozhraní poskytuje plnou funkčnost v podporovaných operačních systémech Windows, na kterých běží .NET Framework (viz článek [.NET Framework požadavky na systém](../get-started/system-requirements.md) nebo verze .NET Core počínaje .net Core 3,0.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní nabízejí určitou podporu pro klientské aplikace Microsoft Active Accessibility prostřednictvím integrované přemostění služby.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Poskytovatelé a klienti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] má čtyři hlavní součásti, jak je znázorněno v následující tabulce.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Rozhraní API zprostředkovatele (UIAutomationProvider. dll a UIAutomationTypes. dll)|Sada definic rozhraní, které jsou implementovány zprostředkovateli automatizace uživatelského rozhraní, objekty, které poskytují informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky a reagují na programové vstupy.|  
|Rozhraní API klienta (UIAutomationClient. dll a UIAutomationTypes. dll)|Sada typů pro spravovaný kód, která umožňuje klientským aplikacím automatizace uživatelského rozhraní získat informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a odeslání vstupu ovládacím prvkům.|  
|UiAutomationCore.dll|Podkladový kód (někdy označovaný jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jádro), který zpracovává komunikaci mezi poskytovateli a klienty.|  
|UIAutomationClientsideProviders.dll|Sada zprostředkovatelů automatizace uživatelského rozhraní pro standardní starší ovládací prvky. (ovládací prvky[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] mají nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Tato podpora je automaticky dostupná pro klientské aplikace.|  
  
 Z pohledu vývojáře softwaru existují dva způsoby použití [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: k vytvoření podpory vlastních ovládacích prvků (pomocí rozhraní API zprostředkovatele) a k vytváření aplikací, které používají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core ke komunikaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky (pomocí rozhraní API klienta). V závislosti na vašem výběru byste se měli podívat na různé části dokumentace. V následujících částech se dozvíte víc o konceptech a získáte praktické znalosti s postupy.  
  
|Část|Předmět|Cílová skupina|  
|-------------|--------------------|--------------|  
|[Základy automatizace uživatelského rozhraní](index.md) (Tato část)|Široké přehledy konceptů.|All.|  
|[Zprostředkovatelé automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-providers-for-managed-code.md)|Přehledy a postupy, které vám pomůžou s používáním rozhraní API pro poskytovatele.|Řízení vývojářů.|  
|[Klienti automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-clients-for-managed-code.md)|Přehledy a postupy, které vám pomůžou s používáním rozhraní API klienta.|Vývojáři klientských aplikací.|  
|[Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns.md)|Informace o tom, jak by měly být implementovány vzory řízení poskytovateli a jaké funkce jsou k dispozici pro klienty.|All.|  
|[Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](ui-automation-text-pattern.md)|Informace o tom, jak by měl být vzor ovládacího prvku textu implementován poskytovateli a jaké funkce jsou k dispozici pro klienty.|All.|  
|[Typy ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types.md)|Informace o vlastnostech a vzorech ovládacích prvků podporovaných různými typy ovládacích prvků.|All.|  
  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obory názvů, knihovny DLL, které je obsahují, a cílovou skupinu, která je používá.  
  
|Obor názvů|Odkazované knihovny DLL|Cílová skupina|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Vývojáři klienta automatizace uživatelského rozhraní; slouží k vyhledání <xref:System.Windows.Automation.AutomationElement> objektů, registraci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ch událostí a práci s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]mi vzory ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro jiné architektury než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro jiné architektury než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; slouží k implementaci vzoru ovládacího prvku TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zpřístupňuje všechny části [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] klientským aplikacím jako <xref:System.Windows.Automation.AutomationElement>. Prvky jsou obsaženy ve stromové struktuře s plochou jako kořenovým elementem. Klienti mohou filtrovat nezpracované zobrazení stromu jako zobrazení ovládacího prvku nebo zobrazení obsahu. Aplikace také mohou vytvářet vlastní zobrazení.  
  
 <xref:System.Windows.Automation.AutomationElement> objekty zpřístupňují společné vlastnosti [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, které představují. Jedna z těchto vlastností je typ ovládacího prvku, který definuje základní vzhled a funkce jako jedinou rozpoznatelnou entitu: například tlačítko nebo zaškrtávací políčko.  
  
 Kromě toho prvky zpřístupňují vzory ovládacích prvků, které poskytují vlastnosti specifické pro jejich typy ovládacích prvků. Vzory ovládacích prvků také zpřístupňují metody, které klientům umožňují získat další informace o elementu a k poskytnutí vstupu.  
  
> [!NOTE]
> Mezi typy ovládacích prvků a vzory ovládacích prvků neexistuje žádná korespondence 1:1. Vzor ovládacího prvku může být podporován více typy ovládacích prvků a ovládací prvek může podporovat více vzorů ovládacích prvků, z nichž každý zveřejňuje různé aspekty jeho chování. Například pole se seznamem má alespoň dva vzory ovládacích prvků: jeden, který představuje jeho schopnost rozbalit a sbalit a druhý, který představuje mechanismus výběru. Konkrétní informace najdete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] také poskytuje informace klientským aplikacím prostřednictvím událostí. Na rozdíl od WinEvents nejsou události [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] založené na mechanizmu všesměrového vysílání. klienti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se registrují pro konkrétní oznámení událostí a můžou požádat o konkrétní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti a informace o vzoru ovládacího prvku budou předány do obslužných rutin událostí. Kromě toho událost [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje odkaz na element, který ji vyvolal. Poskytovatelé můžou zvýšit výkon tím, že vyberou události selektivně v závislosti na tom, jestli některý z klientů naslouchá.  
  
## <a name="see-also"></a>Viz také:

- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md)
- [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md)
- [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md)
