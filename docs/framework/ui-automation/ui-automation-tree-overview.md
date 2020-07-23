---
title: Přehled stromu automatizace uživatelského rozhraní
description: Přečtěte si přehled o stromů automatizace uživatelského rozhraní. Seznamte se s různými zobrazeními stromu automatizace uživatelského rozhraní, jako jsou nezpracovaná zobrazení, ovládací prvky zobrazení a zobrazení obsahu.
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: 0ffe4b4e6157f5bff3284d6978e0ec28641cf72d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924549"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty technologie usnadnění a testovací skripty procházejí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturou a shromažďují informace o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvcích a.  
  
 V rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je kořenový prvek ( <xref:System.Windows.Automation.AutomationElement.RootElement%2A> ), který představuje aktuální plochu a jehož podřízené prvky představují okna aplikací. Každý z těchto podřízených elementů může obsahovat prvky reprezentující některé z prvků [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , jako jsou nabídky, tlačítka, panely nástrojů a seznamy. Tyto prvky mohou obsahovat prvky, jako jsou položky seznamu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom není pevnou strukturou a v jeho úhrnu se zřídka zobrazuje, protože by mohl obsahovat tisíce prvků. Části se sestavují podle potřeby a můžou se měnit jako prvky, které se přidají, přesunou nebo odeberou.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom implementací navigace mezi položkami v rámci fragmentu, která se skládá z kořene (obvykle hostovaného v okně) a podstromu. Nicméně poskytovatelé nejsou dotčeni navigací z jednoho ovládacího prvku na jiný. To je spravováno [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jádrem, a to pomocí informací z výchozích poskytovatelů oken.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Zobrazení stromu automatizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom lze filtrovat a vytvořit tak zobrazení, která obsahují pouze <xref:System.Windows.Automation.AutomationElement> objekty relevantní pro konkrétního klienta. Tento přístup umožňuje klientům přizpůsobit strukturu prezentovanou podle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jejich konkrétních potřeb.  
  
 Klient nástroje má dva způsoby přizpůsobení zobrazení: podle oboru a filtrováním. Rozsah je definující rozsah zobrazení od základního prvku: aplikace může například chtít najít pouze přímé podřízené položky plochy nebo všechny následníky okna aplikace. Filtrování definuje typy prvků, které mají být zahrnuty do zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování definováním vlastností u elementů, včetně <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> vlastností a.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje tři výchozí zobrazení. Tato zobrazení jsou definována typem filtrování provedeno; Rozsah libovolného zobrazení je definován aplikací. Kromě toho může aplikace použít další filtry na vlastnosti; například pro zahrnutí pouze povolených ovládacích prvků do zobrazení ovládacích prvků.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Nezpracované zobrazení  
 Nezpracované zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je úplný strom <xref:System.Windows.Automation.AutomationElement> objektů, pro které je plocha kořenem. Nezpracované zobrazení přesně sleduje nativní programovou strukturu aplikace, a proto je nejpřesnější zobrazení k dispozici. Je to také základ, na kterém jsou sestavena další zobrazení stromu. Vzhledem k tomu, že toto zobrazení závisí na základní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektuře, nezpracovaná zobrazení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítka budou mít jiné nezpracované zobrazení než tlačítko Win32.  
  
 Nezpracované zobrazení se získá tak, že vyhledá prvky bez zadání vlastností nebo pomocí <xref:System.Windows.Automation.TreeWalker.RawViewWalker> pro procházení stromové struktury.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Zobrazení ovládacích prvků  
 Zobrazení ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu zjednodušuje úlohu produktu asistenční technologie, která popisuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] koncovému uživateli a pomáhá tomuto koncovému uživateli interakci s aplikací, protože se úzce mapuje na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] strukturu vnímanou koncovým uživatelem.  
  
 Zobrazení ovládacího prvku je podmnožinou nezpracovaného zobrazení. Obsahuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracovaného zobrazení, které by koncový uživatel rozuměl jako interaktivní nebo přispívá k logické struktuře ovládacího prvku v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Příklady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, které přispívají k logické struktuře [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , ale nejsou interaktivní, jsou kontejnery položek, jako jsou například záhlaví zobrazení seznamu, panely nástrojů, nabídky a stavový řádek. Neinteraktivní položky použité jednoduše pro rozložení nebo dekorativní účely nebudou zobrazeny v zobrazení ovládacího prvku. Příkladem může být panel, který byl použit pouze k rozložení ovládacích prvků v dialogovém okně, ale neobsahuje žádné informace. Neinteraktivní položky, které se zobrazí v zobrazení ovládacího prvku, jsou grafika s informacemi a statický text v dialogovém okně. Neinteraktivní položky, které jsou součástí zobrazení ovládacího prvku, nemohou přijímat fokus klávesnice.  
  
 Zobrazení ovládacího prvku je získáno hledáním prvků, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost nastavenou na `true` nebo pomocí <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> pro procházení stromové struktury.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je podmnožinou zobrazení ovládacího prvku. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které vyjadřují skutečné informace v uživatelském rozhraní, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, které mohou přijímat fokus klávesnice a textu, který není popiskem na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položce. Například hodnoty v rozevíracím seznamu se zobrazí v zobrazení obsahu, protože představují informace používané koncovým uživatelem. V zobrazení obsahu se pole se seznamem a seznam vystupují jako kolekce [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, kde jedna nebo možná více než jedna položka může být vybrána. Fakt, že jeden je vždy otevřený a jeden může rozbalit a sbalit, je v zobrazení obsahu nepodstatný, protože je navržený tak, aby zobrazoval data nebo obsah, který je prezentován uživateli.  
  
 Zobrazení obsahu je získáno vyhledáním prvků, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost nastavenou na `true` nebo pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> pro procházení stromové struktury.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.AutomationElement>
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
