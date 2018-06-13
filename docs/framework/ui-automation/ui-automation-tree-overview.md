---
title: Přehled stromu automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0823a569b19d46f32c1cb780470a935f20429c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409120"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Produktů využívajících technologie usnadnění a skripty, testovací přejděte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu shromažďování informací o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a jejích elementů.  
  
 V rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu existuje je kořenový element (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) představující aktuální ploše a jehož podřízené elementy reprezentují aplikace windows. Každý z těchto podřízených prvků může obsahovat elementy představující kusy [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] například nabídky, tlačítek, panely nástrojů a seznamy. Tyto prvky zase mohou obsahovat prvky například položky seznamu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Není opravené struktura stromu a je málokdy zobrazená v jeho veškeré vzhledem k tomu, že farma může obsahovat tisíce elementy. Části jsou vytvořeny, jako jsou potřeba, a můžete provádět změny, jako jsou elementy přidat, přesunout nebo odebrat.  
  
 Podpora zprostředkovatelů automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu implementací navigace mezi položky v rámci fragment, který se skládá z kořenové (obvykle hostované v okně) a podstrom. Zprostředkovatelé však nejsou nevadí navigační z jednoho ovládacího prvku do jiného. Spravuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní, pomocí informací z výchozí okno zprostředkovatele.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Zobrazení stromu automatizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Stromu je možné filtrovat vytvořte zobrazení, které obsahují pouze ty <xref:System.Windows.Automation.AutomationElement> objekty, které jsou relevantní pro konkrétního klienta. Tento přístup umožňuje klientům přizpůsobit strukturu nabízena prostřednictvím [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] svých konkrétních potřeb.  
  
 Klient má dva způsoby přizpůsobení zobrazení: podle rozsahu a filtrování. Obor definuje rozsah zobrazení, od base element:, aplikace může například najít pouze přímé podřízené objekty plochy, nebo všech potomků okna aplikace. Filtrování je definování typů elementů, které mají být zahrnuty v zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování podle u elementů, včetně definování vlastností <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> a <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> vlastnosti.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje tři výchozí zobrazení. Tato zobrazení jsou definovány podle typu filtrování provést; rozsah všechna zobrazení, je definován v aplikaci. Kromě toho aplikace můžete použít jiné filtry na vlastnosti; například obsahovat pouze povolené ovládacích prvků v zobrazení ovládacího prvku.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Nezpracovaná zobrazení  
 Nezpracovaná zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je stromu úplné <xref:System.Windows.Automation.AutomationElement> objekty, pro které ploše je kořenový adresář. Nezpracovaná zobrazení přesně dodržuje strukturu nativní programový aplikace a proto je nejvíce podrobné zobrazení k dispozici. Je také základ, na kterém jsou vytvořené zobrazení stromu. Protože toto zobrazení, závisí na základní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, nezpracovaná zobrazení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítko bude mít jiné nezpracovaná zobrazení než [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tlačítko.  
  
 Nezpracovaná zobrazení se získávají pomocí vyhledávání elementů bez zadání vlastnosti nebo pomocí <xref:System.Windows.Automation.TreeWalker.RawViewWalker> přejděte stromu.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Zobrazení ovládacího prvku  
 Zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu zjednodušuje úkol produktů využívajících technologie usnadnění popisující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pro koncové uživatele a pomáhají tento koncový uživatel spolupracovat s aplikací, protože úzce mapuje na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktura jak jej koncový uživatel.  
  
 Zobrazení ovládacího prvku je podmnožinou nezpracovaná zobrazení. Obsahuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracovaná zobrazení, které by koncový uživatel pochopit jako interaktivní nebo přispívajících logické struktura ovládacího prvku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Příklady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které přispívají k logické struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nejsou interaktivní sami, jsou kontejnery položek, jako jsou záhlaví zobrazení seznamu, panely nástrojů, nabídky a na stavovém řádku. Neinteraktivně položky používá jednoduše pro rozložení nebo dekorativní účely nedostupné v zobrazení ovládacího prvku. Příklad je panel, který byl použit pouze pro Rozvrhněte ovládací prvky v dialogu, ale ne samotný neobsahuje žádné informace. Neinteraktivně položky, které se zobrazí v zobrazení ovládacího prvku jsou grafiky s informacemi a statický text v dialogu. Neinteraktivně položky, které jsou zahrnuty v zobrazení ovládacího prvku nemůže přijímat fokus klávesnice.  
  
 Zobrazení ovládacího prvku se získá tak, že prvky, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost nastavena na hodnotu `true`, nebo pomocí <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> přejděte stromu.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je podmnožinou zobrazení ovládacího prvku. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které oznamují true informace v uživatelském rozhraní, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které můžou přijímat klávesové fokus a některé text, který není na štítek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky. Například hodnoty v rozevíracím seznamem se zobrazí v zobrazení obsahu, protože představují informace používá koncový uživatel. V zobrazení obsahu pole se seznamem a seznam jsou obě vyjádřené kolekce [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, kde lze vybrat jednu nebo možná více než jednu položku. Skutečnost, že jeden je vždy otevřený a jeden můžete rozbalit nebo sbalit je důležité v zobrazení obsahu, protože je určen k zobrazení dat nebo obsahu, který má problém pro uživatele.  
  
 Zobrazení obsahu se získá tak, že prvky, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost nastavena na hodnotu `true`, nebo pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> přejděte stromu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.AutomationElement>  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
