---
title: Přehled stromu automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: d1edbb82e0d5d6a6275c09646fbf8e54b4ff90df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800290"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty a testovací skripty pro asistenční technologie umožňují procházet strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a získat informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a jeho prvcích.  
  
 Ve stromové struktuře [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] existuje kořenový element (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>), který představuje aktuální plochu a jejíž podřízené prvky představují okna aplikací. Každý z těchto podřízených elementů může obsahovat prvky reprezentující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], jako jsou nabídky, tlačítka, panely nástrojů a seznamy. Tyto prvky mohou obsahovat prvky, jako jsou položky seznamu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom není pevnou strukturou a v jeho celkovém poměru se zřídka zobrazuje, protože by mohl obsahovat tisíce prvků. Části se sestavují podle potřeby a můžou se měnit jako prvky, které se přidají, přesunou nebo odeberou.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tím, že implementují navigaci mezi položkami v rámci fragmentu, která se skládá z kořene (obvykle hostovaného v okně) a podstromu. Nicméně poskytovatelé nejsou dotčeni navigací z jednoho ovládacího prvku na jiný. To je spravováno [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core s využitím informací z výchozích poskytovatelů oken.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Zobrazení stromu automatizace  
 Strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lze filtrovat, chcete-li vytvořit zobrazení, která obsahují pouze objekty <xref:System.Windows.Automation.AutomationElement> relevantní pro konkrétního klienta. Tento přístup umožňuje klientům přizpůsobit strukturu, kterou prezentují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podle jejich konkrétních potřeb.  
  
 Klient nástroje má dva způsoby přizpůsobení zobrazení: podle oboru a filtrováním. Rozsah je definující rozsah zobrazení od základního prvku: aplikace může například chtít najít pouze přímé podřízené položky plochy nebo všechny následníky okna aplikace. Filtrování definuje typy prvků, které mají být zahrnuty do zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování definováním vlastností u elementů, včetně vlastností <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> a <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje tři výchozí zobrazení. Tato zobrazení jsou definována typem filtrování provedeno; Rozsah libovolného zobrazení je definován aplikací. Kromě toho může aplikace použít další filtry na vlastnosti; například pro zahrnutí pouze povolených ovládacích prvků do zobrazení ovládacích prvků.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Nezpracované zobrazení  
 Nezpracované zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je úplný strom <xref:System.Windows.Automation.AutomationElement> objektů, pro které je plocha kořenem. Nezpracované zobrazení přesně sleduje nativní programovou strukturu aplikace, a proto je nejpřesnější zobrazení k dispozici. Je to také základ, na kterém jsou sestavena další zobrazení stromu. Vzhledem k tomu, že toto zobrazení závisí na základní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Framework, nezpracované zobrazení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítka bude mít jiné nezpracované zobrazení než tlačítko [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].  
  
 Nezpracovaná zobrazení se získávají hledáním elementů bez zadání vlastností nebo pomocí <xref:System.Windows.Automation.TreeWalker.RawViewWalker> k procházení stromu.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Zobrazení ovládacích prvků  
 Zobrazení ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ového stromu zjednodušuje úlohu produktu asistenční technologie s popisem [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] koncovému uživateli a pomáhá tomuto koncovému uživateli pracovat s aplikací, protože se úzce mapuje na strukturu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vnímanou koncovým uživatelem.  
  
 Zobrazení ovládacího prvku je podmnožinou nezpracovaného zobrazení. Zahrnuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracovaného zobrazení, které by koncový uživatel rozuměl jako interaktivní nebo přispívá k logické struktuře ovládacího prvku v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Příklady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ch položek, které přispívají k logické struktuře [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nejsou interaktivní, jsou kontejnery položek, jako jsou například záhlaví zobrazení seznamu, panely nástrojů, nabídky a stavový řádek. Neinteraktivní položky použité jednoduše pro rozložení nebo dekorativní účely nebudou zobrazeny v zobrazení ovládacího prvku. Příkladem může být panel, který byl použit pouze k rozložení ovládacích prvků v dialogovém okně, ale neobsahuje žádné informace. Neinteraktivní položky, které se zobrazí v zobrazení ovládacího prvku, jsou grafika s informacemi a statický text v dialogovém okně. Neinteraktivní položky, které jsou součástí zobrazení ovládacího prvku, nemohou přijímat fokus klávesnice.  
  
 Zobrazení ovládacího prvku se získá tak, že se vyhledají prvky, které mají vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> nastavenou na `true`, nebo pomocí <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> k procházení stromu.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je podmnožinou zobrazení ovládacího prvku. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které dodávají skutečné informace v uživatelském rozhraní, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, které mohou přijímat fokus klávesnice a nějaký text, který není popisek pro [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položku. Například hodnoty v rozevíracím seznamu se zobrazí v zobrazení obsahu, protože představují informace používané koncovým uživatelem. V zobrazení obsahu se pole se seznamem a seznam zobrazují jako kolekce [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ch položek, kde jedna nebo možná více než jedna položka může být vybrána. Fakt, že jeden je vždy otevřený a jeden může rozbalit a sbalit, je v zobrazení obsahu nepodstatný, protože je navržený tak, aby zobrazoval data nebo obsah, který je prezentován uživateli.  
  
 Zobrazení obsahu se získá vyhledáním prvků, které mají vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> nastavenou na hodnotu `true`nebo pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> k procházení stromu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.AutomationElement>
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
