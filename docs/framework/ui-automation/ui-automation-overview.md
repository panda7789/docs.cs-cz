---
title: Přehled automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 968660f2fa043ee4028cb144f368d9380729ffef
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133803"
---
# <a name="ui-automation-overview"></a>Přehled automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]je novým rozhraním usnadnění pro [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], které je k dispozici ve všech [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]operačních systémech, které podporují.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje programový přístup k [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] většině prvků na ploše a umožňuje produktům asistenční technologie, jako jsou čtečky obrazovky, poskytovat informace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] o koncových uživatelích [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a manipulaci s tím, že se jedná o jiné než standardní vstup. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje také automatizovaným testovacím skriptům pracovat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]s.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]neumožňuje komunikaci mezi procesy spuštěnými různými uživateli prostřednictvím příkazu **Spustit jako** .  
  
 Klientské aplikace automatizace uživatelského rozhraní lze zapsat s jistotou, že budou fungovat na více architekturách. Základní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] masky jsou jakékoli rozdíly v rozhraních, které jsou základem různých [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]částí. `Content` Například [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítka <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, vlastnost`Caption` tlačítkaa`ALT` vlastnost obrázku HTML jsou namapovány na jedinou vlastnost, v zobrazení. [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]  
  
Automatizace uživatelského rozhraní poskytuje plnou funkčnost v podporovaných operačních systémech Windows, na kterých běží .NET Framework (viz článek [.NET Framework požadavky na systém](../get-started/system-requirements.md) nebo verze .NET Core počínaje .net Core 3,0.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní nabízejí určitou podporu pro klientské aplikace Microsoft Active Accessibility prostřednictvím integrované přemostění služby.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Poskytovatelé a klienti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]má čtyři hlavní součásti, jak je znázorněno v následující tabulce.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Rozhraní API zprostředkovatele (UIAutomationProvider. dll a UIAutomationTypes. dll)|Sada definic rozhraní, které jsou implementovány zprostředkovateli automatizace uživatelského rozhraní, objekty, které poskytují [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] informace o prvcích a reagují na programové vstupy.|  
|Rozhraní API klienta (UIAutomationClient. dll a UIAutomationTypes. dll)|Sada typů pro spravovaný kód, která umožňuje klientským aplikacím automatizace uživatelského rozhraní získat informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a k odeslání vstupu ovládacím prvkům.|  
|UiAutomationCore.dll|Podkladový kód (někdy označovaný jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jádro), který zpracovává komunikaci mezi poskytovateli a klienty.|  
|UIAutomationClientsideProviders.dll|Sada zprostředkovatelů automatizace uživatelského rozhraní pro standardní starší ovládací prvky. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mají nativní podporu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pro.) Tato podpora je automaticky dostupná pro klientské aplikace.|  
  
 Z pohledu vývojáře softwaru existují dva způsoby použití [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: k vytvoření podpory vlastních ovládacích prvků (pomocí rozhraní API zprostředkovatele) a k vytváření aplikací, které [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] používají jádro ke komunikaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky (pomocí rozhraní API klienta). V závislosti na vašem výběru byste se měli podívat na různé části dokumentace. V následujících částech se dozvíte víc o konceptech a získáte praktické znalosti s postupy.  
  
|Section|Předmět|Cílová skupina|  
|-------------|--------------------|--------------|  
|[Základy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md) (Tato část)|Široké přehledy konceptů.|Všechny.|  
|[Zprostředkovatelé automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Přehledy a postupy, které vám pomůžou s používáním rozhraní API pro poskytovatele.|Řízení vývojářů.|  
|[Klienti automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Přehledy a postupy, které vám pomůžou s používáním rozhraní API klienta.|Vývojáři klientských aplikací.|  
|[Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informace o tom, jak by měly být implementovány vzory řízení poskytovateli a jaké funkce jsou k dispozici pro klienty.|Všechny.|  
|[Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informace o tom, jak by měl být vzor ovládacího prvku textu implementován poskytovateli a jaké funkce jsou k dispozici pro klienty.|Všechny.|  
|[Typy ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informace o vlastnostech a vzorech ovládacích prvků podporovaných různými typy ovládacích prvků.|Všechny.|  
  
 V následující tabulce jsou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uvedeny obory názvů, knihovny DLL, které je obsahují, a cílová skupina, která je používá.  
  
|Obor názvů|Odkazované knihovny DLL|Cílová skupina|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Vývojáři klienta automatizace uživatelského rozhraní; slouží k vyhledání <xref:System.Windows.Automation.AutomationElement> objektů, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] registraci událostí a práci se [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzorci ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro jiné architektury než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro jiné architektury než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; používané k implementaci vzoru ovládacího prvku TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]pro.|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zpřístupňuje všechny součásti [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] klientských aplikací <xref:System.Windows.Automation.AutomationElement>jako. Prvky jsou obsaženy ve stromové struktuře s plochou jako kořenovým elementem. Klienti mohou filtrovat nezpracované zobrazení stromu jako zobrazení ovládacího prvku nebo zobrazení obsahu. Aplikace také mohou vytvářet vlastní zobrazení.  
  
 <xref:System.Windows.Automation.AutomationElement>objekty zpřístupňují společné vlastnosti [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvků, které představují. Jedna z těchto vlastností je typ ovládacího prvku, který definuje základní vzhled a funkce jako jedinou rozpoznatelnou entitu: například tlačítko nebo zaškrtávací políčko.  
  
 Kromě toho prvky zpřístupňují vzory ovládacích prvků, které poskytují vlastnosti specifické pro jejich typy ovládacích prvků. Vzory ovládacích prvků také zpřístupňují metody, které klientům umožňují získat další informace o elementu a k poskytnutí vstupu.  
  
> [!NOTE]
> Mezi typy ovládacích prvků a vzory ovládacích prvků neexistuje žádná korespondence 1:1. Vzor ovládacího prvku může být podporován více typy ovládacích prvků a ovládací prvek může podporovat více vzorů ovládacích prvků, z nichž každý zveřejňuje různé aspekty jeho chování. Například pole se seznamem má alespoň dva vzory ovládacích prvků: jeden, který představuje jeho schopnost rozbalit a sbalit a druhý, který představuje mechanismus výběru. Konkrétní informace najdete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje také informace klientským aplikacím prostřednictvím událostí. Na rozdíl [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)]od [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , události nejsou založené na mechanismu vysílání. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Klienti se registrují pro konkrétní oznámení událostí a můžou požádat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o konkrétní vlastnosti a informace o vzoru ovládacího prvku, které se předají do obslužných rutin událostí. Kromě toho [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost obsahuje odkaz na element, který ji vyvolal. Poskytovatelé můžou zvýšit výkon tím, že vyberou události selektivně v závislosti na tom, jestli některý z klientů naslouchá.  
  
## <a name="see-also"></a>Viz také:

- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
