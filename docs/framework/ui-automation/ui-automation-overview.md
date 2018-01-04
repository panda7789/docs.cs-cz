---
title: "Přehled automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
caps.latest.revision: "35"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d86c70ec4421bc716b12044bac30f8f925c375f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-overview"></a>Přehled automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]je nové architektury usnadnění [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], k dispozici ve všech operačních systémech, které podporují [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zajišťují programový přístup k většině [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy na ploše, například povolení produktů využívajících technologie usnadnění obrazovky čtečky k poskytování informací o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] koncovým uživatelům a k manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nástrojem znamená jiné než standardní vstup. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]také umožňuje skripty automatizovaných testů pro interakci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]neumožňuje komunikaci mezi procesy spuštěné různými uživateli prostřednictvím **spustit jako** příkaz.  
  
 Automatizace uživatelského rozhraní klientské aplikace může být napsán s záruku, že bude fungovat na více rozhraní. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní zakrývá případné rozdíly v rozhraní, které tvoří základ různými [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Například `Content` vlastnost [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítko `Caption` vlastnost [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tlačítko a `ALT` vlastnost bitové kopie HTML jsou namapované na jednu vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje úplné funkce v [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], a [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Zprostředkovatelé automatizace uživatelského rozhraní nabízejí některé podpora [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] klientské aplikace, pomocí předdefinovaných přemostění služby.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Zprostředkovatelé a klientů  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]má čtyři hlavní součásti, jak je znázorněno v následující tabulce.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Zprostředkovatel [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll a UIAutomationTypes.dll)|Sada rozhraní definice, které jsou implementované ve zprostředkovateli automatizace uživatelského rozhraní, objekty, které poskytují informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy a reakce na programový vstup.|  
|Klientské rozhraní API (UIAutomationClient.dll a UIAutomationTypes.dll)|Sadu typů pro spravovaný kód, který umožňuje získat informace o automatizace uživatelského rozhraní klientské aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a k odeslání vstupu pro ovládací prvky.|  
|Knihovna UiAutomationCore.dll|Kódu (někdy nazývané [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní), která zpracovává komunikaci mezi poskytovatelů a klienty.|  
|UIAutomationClientsideProviders.dll|Sada zprostředkovatelů automatizace uživatelského rozhraní pro standardní ovládací prvky starší verze. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají nativní podpora pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Tato podpora je automaticky dostupný pro klientské aplikace.|  
  
 Z hlediska vyvíjející software, existují dva způsoby použití [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: vytvoření podporu pro vlastní ovládací prvky (použití zprostředkovatele rozhraní API) a vytváření aplikací, které používají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní ke komunikaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky (použití klient rozhraní API). V závislosti na vaší fokus se seznamte s různým částem v dokumentaci. Můžete další informace o konceptech a získají praktické postupy informace v následujících částech.  
  
|Část|Předmět|Cílová skupina|  
|-------------|--------------------|--------------|  
|[Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md) (této části)|Široký přehled konceptů.|Všechny.|  
|[Zprostředkovatelé automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Přehled a postupy vám pomohou používat API poskytovatele.|Vývojáři ovládacího prvku.|  
|[Klienti automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Přehled a postupy vám pomohou používat klientského rozhraní API.|Vývojáři klientské aplikace.|  
|[Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informace o tom, jak by měla být implementována vzory ovládacích prvků zprostředkovatelé a jaké funkce je k dispozici pro klienty.|Všechny.|  
|[Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informace o tom, jak by měla být implementována textu – vzor ovládacích prvků zprostředkovatelé a jaké funkce je k dispozici pro klienty.|Všechny.|  
|[Typy ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informace o vlastnosti a řízení vzory podporuje různé typy ovládacích prvků.|Všechny.|  
  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obory názvů, knihovny DLL, které obsahují a cílovou skupinu, která používá je.  
  
|Obor názvů|Odkazované knihovny DLL|Cílová skupina|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Automatizace uživatelského rozhraní klienta vývojářů. použít k vyhledání <xref:System.Windows.Automation.AutomationElement> objekty, registrace pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události a můžete pracovat s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro rozhraní než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro rozhraní než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; použité k implementaci vzoru TextPattern ovládacích prvků.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Každá část zpřístupní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pro klientské aplikace jako <xref:System.Windows.Automation.AutomationElement>. Elementy jsou obsažené ve stromové struktuře, s plochou jako kořenový element. Klienty můžete filtrovat nezpracovaná zobrazení stromu jako zobrazení ovládacího prvku nebo zobrazení obsahu. Aplikace můžete také vytvořit vlastní zobrazení.  
  
 <xref:System.Windows.Automation.AutomationElement>objekty vystavit běžné vlastnosti [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] představují elementy. Jednu z těchto vlastností je typ ovládacího prvku, který definuje základní vzhled a funkce jako jedna entita rozpoznatelném: například tlačítko nebo zaškrtávací políčko.  
  
 Kromě toho elementy vystavit vzory ovládacích prvků, které poskytují vlastnosti specifické pro jejich typy ovládacích prvků. Vzory ovládacích prvků vystavit také metody, které umožní klientům získat další informace o elementu a umožní zadání vstupu.  
  
> [!NOTE]
>  Neexistuje žádná souvislosti mezi typy ovládacích prvků a vzory ovládacích prvků. Vzor ovládacích prvků může podporovat více typy ovládacích prvků a ovládacího prvku mohou podporovat více vzorů ovládacích prvků, každý z nich vystavuje různých aspektů své chování. Například pole se seznamem má alespoň dva vzory ovládacích prvků: jeden, který představuje schopnost rozbalení a sbalení a druhé, které představuje mechanismus výběru. Konkrétní informace naleznete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]také poskytuje informace pro klientské aplikace prostřednictvím událostí. Na rozdíl od [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které nejsou založené na mechanismu požadavek všesměrového vysílání. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Klienti zaregistrovat pro konkrétní události oznámení a může tento konkrétní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti a řízení vzor předávat do jejich obslužné rutiny událostí. Kromě toho [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí obsahuje odkaz na element, který je vyvolána. Zprostředkovatelé lze vylepšit výkon vyvolávání událostí selektivně, v závislosti na tom, jestli jsou všechny klienty naslouchá.  
  
## <a name="see-also"></a>Viz také  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
