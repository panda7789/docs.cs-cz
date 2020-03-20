---
title: Přehled automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 6f938302967e1b519105769717d326e5042a7bce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179922"
---
# <a name="ui-automation-overview"></a>Přehled automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]je nová architektura usnadnění pro systém Microsoft Windows, která je k dispozici ve všech operačních systémech, které podporují [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Poskytuje programový přístup [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] k většině prvků na ploše, což umožňuje asistenční technologie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] produkty, jako jsou programy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pro čtení z obrazovky poskytovat informace o koncových uživatelů a manipulovat pomocí jinými než standardní vstup. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje také automatickou testovací skripty pro interakci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]neumožňuje komunikaci mezi procesy spuštěnými různými uživateli prostřednictvím příkazu **Spustit jako.**  
  
 Klientské aplikace automatizace uživatelského rozhraní lze zapsat s jistotou, že budou pracovat na více architekturách. Jádro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] maskuje všechny rozdíly v rámcích, které [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]jsou základem různých kusů . Například `Content` vlastnost [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítka, `Caption` vlastnost tlačítka Win32 a `ALT` vlastnost obrazu HTML jsou mapovány na jednu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>vlastnost , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v zobrazení.  
  
Automatizace uživatelského rozhraní poskytuje plnou funkčnost v podporovaných operačních systémech Windows se systémem .NET Framework (viz [požadavky na systém rozhraní .NET Framework](../get-started/system-requirements.md) nebo verze rozhraní .NET Core začínající mise .NET Core 3.0.  
  
 Poskytovatelé automatizace uživatelského rozhraní nabízejí určitou podporu klientských aplikací Microsoft Active Accessibility prostřednictvím integrované přemosťovací služby.  
  
<a name="Providers_and_Clients"></a>
## <a name="providers-and-clients"></a>Poskytovatelé a klienti  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]má čtyři hlavní součásti, jak je znázorněno v následující tabulce.  
  
|Komponenta|Popis|  
|---------------|-----------------|  
|Rozhraní API zprostředkovatele (UIAutomationProvider.dll a UIAutomationTypes.dll)|Sada definic rozhraní, které jsou implementovány zprostředkovateli automatizace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uživatelského rozhraní, objekty, které poskytují informace o prvky a reagovat na programový vstup.|  
|Rozhraní API klienta (UIAutomationClient.dll a UIAutomationTypes.dll)|Sada typů spravovaného kódu, která umožňuje klientským aplikacím [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] automatizace uživatelského rozhraní získat informace o a odesílat vstup ovládacím prvkům.|  
|Soubor UiAutomationCore.dll|Základní kód (někdy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nazývaný jádro), který zpracovává komunikaci mezi zprostředkovateli a klienty.|  
|Soubor DLL UIAutomationClientsideProviders.dll|Sada zprostředkovatelů automatizace uživatelského rozhraní pro standardní starší ovládací prvky. (ovládací[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] prvky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]mají nativní podporu pro .) Tato podpora je automaticky k dispozici klientským aplikacím.|  
  
 Z pohledu vývojáře softwaru existují dva [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]způsoby použití : k vytvoření podpory pro vlastní ovládací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky (pomocí rozhraní API zprostředkovatele) a vytváření aplikací, které používají jádro ke komunikaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky (pomocí klientského rozhraní API). V závislosti na zaměření byste měli odkazovat na různé části dokumentace. Další informace o konceptech a praktické znalosti o tom získáte v následujících částech.  
  
|Sekce|Předmět|Cílová skupina|  
|-------------|--------------------|--------------|  
|[Základy automatizace uživatelského rozhraní](index.md) (tato část)|Široké přehledy pojmů.|Všechny.|  
|[Zprostředkovatelé automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-providers-for-managed-code.md)|Přehledy a témata s postupy, které vám pomůžou používat rozhraní API zprostředkovatele.|Řídit vývojáře.|  
|[Klienti automatizace uživatelského rozhraní pro spravovaný kód](ui-automation-clients-for-managed-code.md)|Přehledy a témata s postupy, které vám pomohou používat rozhraní API klienta.|Vývojáři klientských aplikací.|  
|[Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns.md)|Informace o tom, jak by měly být implementovány vzory ovládacích prvku zprostředkovateli a jaké funkce jsou klientům k dispozici.|Všechny.|  
|[Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](ui-automation-text-pattern.md)|Informace o tom, jak text ovládací prvek vzor by měl být implementován zprostředkovateli a jaké funkce je k dispozici klientům.|Všechny.|  
|[Typy ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types.md)|Informace o vlastnostech a vzorcích ovládacích prvku podporovaných různými typy ovládacích prvku.|Všechny.|  
  
 V následující [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabulce jsou uvedeny obory názvů, knihovny DLL, které je obsahují, a cílová skupina, která je používá.  
  
|Obor názvů|Odkazované knihovny DLL|Cílová skupina|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypy|Vývojáři klientů automatizace uživatelského rozhraní; slouží k <xref:System.Windows.Automation.AutomationElement> hledání objektů, registraci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí a práci se vzory ovládacího prvku.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]rozhraní pro jiné rámce než .|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypy|Vývojáři poskytovatelů automatizace uživatelského [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]rozhraní pro jiné rámce než ; slouží k implementaci textpattern ovládacího prvku.|  
|<xref:System.Windows.Automation.Peers>|Presentationframework|Vývojáři poskytovatelů automatizace [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]uživatelského rozhraní pro .|  
  
<a name="UI_Automation_Model"></a>
## <a name="ui-automation-model"></a>Model automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zpřístupní každý [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kus klientských <xref:System.Windows.Automation.AutomationElement>aplikací jako . Prvky jsou obsaženy ve stromové struktuře, s plochou jako kořenový prvek. Klienti mohou filtrovat nezpracované zobrazení stromu jako zobrazení ovládacího prvku nebo zobrazení obsahu. Aplikace mohou také vytvářet vlastní zobrazení.  
  
 <xref:System.Windows.Automation.AutomationElement>objekty zveřejňují [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] společné vlastnosti prvků, které představují. Jednou z těchto vlastností je typ ovládacího prvku, který definuje jeho základní vzhled a funkce jako jednu rozpoznatelnou entitu: například tlačítko nebo zaškrtávací políčko.  
  
 Kromě toho prvky vystavit vzorky ovládacího prvku, které poskytují vlastnosti specifické pro jejich typy ovládacích prvků. Vzory ovládacího prvku také vystavit metody, které umožňují klientům získat další informace o prvku a poskytnout vstup.  
  
> [!NOTE]
> Neexistuje shoda 1:1 mezi typy ovládacích prvku a vzory ovládacího prvku. Vzor ovládacího prvku může být podporován více typů ovládacích prvku a ovládací prvek může podporovat více vzorů ovládacího prvku, z nichž každý zveřejňuje různé aspekty jeho chování. Například pole se seznamem má alespoň dva vzory ovládacího prvku: jeden, který představuje jeho schopnost rozbalit a sbalit a jiný, který představuje mechanismus výběru. Podrobnosti naleznete v [tématu Typy řízení automatizace uživatelského rozhraní](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje také informace klientským aplikacím prostřednictvím událostí. Na rozdíl [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] od WinEvents události nejsou založeny na mechanismu vysílání. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]klienti se zaregistrují pro konkrétní oznámení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí a mohou požadovat, aby určité vlastnosti a informace o vzoru ovládacího prvku byly předány do obslužných rutin událostí. Kromě toho [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost obsahuje odkaz na prvek, který ji vyvolal. Zprostředkovatelé mohou zlepšit výkon tím, že zvýší události selektivně, v závislosti na tom, zda jsou všechny klienty naslouchání.  
  
## <a name="see-also"></a>Viz také

- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md)
- [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md)
- [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md)
