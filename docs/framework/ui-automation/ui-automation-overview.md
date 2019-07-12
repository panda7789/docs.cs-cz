---
title: Přehled automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 02700c75152c32ebee3a0898de1e322ddf9b6e17
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802234"
---
# <a name="ui-automation-overview"></a>Přehled automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je nový rámec usnadnění pro [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], která je dostupná ve všech operačních systémech, které podporují [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje programový přístup k většině [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy ve stolním počítači, jako například povolení produktů využívajících technologie usnadnění obrazovky čtenáři k poskytnutí informací o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] koncovým uživatelům a k manipulaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] formou jiné než standardní vstup. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] také umožňuje automatizované testovací skripty pracovat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] není k umožnění komunikace mezi procesy spuštěné různé uživateli prostřednictvím **spustit jako** příkazu.  
  
 Automatizace uživatelského rozhraní klientské aplikace mohou být zapsaný s jistotu, že bude fungovat na více platforem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core zakrývá případné rozdíly v rozhraní, které tvoří základ různé [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Například `Content` vlastnost [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítko, `Caption` vlastnost [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tlačítko a `ALT` vlastnosti obrázku ve formátu HTML jsou namapovány na jedinou vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje všechny funkce v [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], a [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Zprostředkovatelé automatizace uživatelského rozhraní nabízí některé podporu pro Microsoft Active Accessibility klientské aplikace pomocí integrované služby přemostění Datacenter.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Poskytovatelé a klientů  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] má čtyři hlavní součásti, jak je znázorněno v následující tabulce.  
  
|Součást|Popis|  
|---------------|-----------------|  
|Zprostředkovatel [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider.dll a UIAutomationTypes.dll)|Sada definic rozhraní, které jsou implementované ve zprostředkovateli automatizace uživatelského rozhraní, objekty, které poskytují informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy a reagovat na vstup prostřednictvím kódu programu.|  
|Klientské rozhraní API (UIAutomationClient.dll a UIAutomationTypes.dll)|Sadu typů pro spravovaný kód, který umožňuje automatizaci uživatelského rozhraní klientských aplikací získat informace o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a posílat vstupu pro ovládací prvky.|  
|UiAutomationCore.dll|Základní kód (říká se jim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core), který zpracovává vnitřní komunikaci mezi klienty a poskytovatelů.|  
|UIAutomationClientsideProviders.dll|Sada zprostředkovatelů automatizace uživatelského rozhraní pro standardní ovládací prvky starší verze. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mají nativní podporu pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Tato podpora je automaticky dostupný pro klientské aplikace.|  
  
 Z pohledu vývojáře softwaru, existují dva způsoby použití [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: vytvoření podpory pro vlastní ovládací prvky (pomocí rozhraní API poskytovatele) a vytváření aplikací, které používají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core ke komunikaci s [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy (s použitím rozhraní API klienta). V závislosti na vaší fokus by měla odkazovat na různé části dokumentace. Můžete další informace o konceptech a získat praktické znalosti postupy v následujících částech.  
  
|Section|Odborník na danou|Cílová skupina|  
|-------------|--------------------|--------------|  
|[Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md) (v této části)|Široký přehled konceptů.|Všechny.|  
|[Zprostředkovatelé automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)|Přehledy a postupy: témata vám pomůžou používat rozhraní API poskytovatele.|Vývojáři ovládacího prvku.|  
|[Klienti automatizace uživatelského rozhraní pro spravovaný kód](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md)|Přehledy a postupy: témata vám pomůžou používat rozhraní API klienta.|Vývojáři klientských aplikací.|  
|[Vzory ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)|Informace o tom, jak by měla být implementována vzorů ovládacích prvků poskytovateli a jaké funkce jsou k dispozici pro klienty.|Všechny.|  
|[Vzor ovládacích prvků text pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)|Informace o jak vzoru ovládacích prvků Text by měla být implementována poskytovateli a jaké funkce jsou k dispozici pro klienty.|Všechny.|  
|[Typy ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md)|Informace o vzorech vlastností a ovládací prvek podporuje různé typy ovládacích prvků.|Všechny.|  
  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obory názvů, knihovny DLL, které obsahují a cílovou skupinu, která je používá.  
  
|Obor názvů|Odkazované knihovny DLL|Cílová skupina|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Automatizace uživatelského rozhraní klienta vývojářů. použije k zjištění <xref:System.Windows.Automation.AutomationElement> objekty, zaregistrujte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události a pracovat s [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro rámce jiné než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro rámce jiné než [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; slouží k implementaci vzoru ovládacího prvku TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Vývojáři zprostředkovatelů automatizace uživatelského rozhraní pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Model automatizace uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Každá část zpřístupňuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pro klientské aplikace jako <xref:System.Windows.Automation.AutomationElement>. Prvky jsou obsaženy ve stromové struktuře, s plochou, jako kořenový element. Klienty můžete filtrovat nezpracované zobrazení stromu jako ovládací prvek zobrazení nebo zobrazení obsahu. Aplikace můžete také vytvořit vlastní zobrazení.  
  
 <xref:System.Windows.Automation.AutomationElement> objekty vystavit běžné vlastnosti [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky, které představují. Jednu z těchto vlastností je typ ovládacího prvku, který definuje jeho základní vzhled a funkce jako jedna entita rozpoznatelných: například tlačítko nebo zaškrtnutí políčka.  
  
 Kromě toho prvky vystavit vzorů ovládacích prvků, které poskytuje vlastnosti specifické pro jejich typy ovládacích prvků. Vzory ovládacích prvků také vystavit metody, které umožňují klientům, chcete-li získat další informace o elementu a umožní zadání vstupu.  
  
> [!NOTE]
>  Není shoda mezi typy ovládacích prvků a vzorů ovládacích prvků. Vzor ovládacích prvků může podporovat více typů ovládacích prvků a ovládací prvek může podporovat více vzorů ovládacích prvků, každý z nich vystavuje různé aspekty chování. Například pole se seznamem obsahuje alespoň dvě vzorů ovládacích prvků: ten, který představuje jeho schopnosti rozbalíte nebo sbalíte a další vlastnost, která představuje mechanismus výběru. Konkrétní informace naleznete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] také obsahuje informace, které klientské aplikace prostřednictvím událostí. Na rozdíl od [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události nejsou založené na mechanismus všesměrového vysílání. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Klienti registrace k oznámením určité události a můžete požádat o tuto konkrétní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností a ovládacího prvku vzor předávat do jejich obslužné rutiny událostí. Kromě toho [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost obsahuje odkaz na prvek, která ji vyvolala. Vyvolávání událostí selektivně, v závislosti na tom, zda všech klientů, kteří naslouchají výkon lze zvýšit poskytovatelů.  
  
## <a name="see-also"></a>Viz také:

- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
