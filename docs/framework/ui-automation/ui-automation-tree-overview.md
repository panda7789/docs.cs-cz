---
title: Přehled stromu automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: adb1d10e659254b5fa326e7c598107d768aa2685
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040398"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Produkty technologie usnadnění a testovací skripty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] procházejí stromovou strukturou a shromažďují informace [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] o prvcích a.  
  
 V rámci<xref:System.Windows.Automation.AutomationElement.RootElement%2A>stromu je kořenový prvek (), který představuje aktuální plochu a jehož podřízené prvky představují okna aplikací. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Každý z těchto podřízených elementů může obsahovat prvky reprezentující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] některé z prvků, jako jsou nabídky, tlačítka, panely nástrojů a seznamy. Tyto prvky mohou obsahovat prvky, jako jsou položky seznamu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom není pevnou strukturou a v jeho úhrnu se zřídka zobrazuje, protože by mohl obsahovat tisíce prvků. Části se sestavují podle potřeby a můžou se měnit jako prvky, které se přidají, přesunou nebo odeberou.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporují strom implementací navigace mezi položkami v rámci fragmentu, která se skládá z kořene (obvykle hostovaného v okně) a podstromu. Nicméně poskytovatelé nejsou dotčeni navigací z jednoho ovládacího prvku na jiný. To je spravováno [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jádrem, a to pomocí informací z výchozích poskytovatelů oken.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Zobrazení stromu automatizace  
 Strom lze filtrovat a vytvořit tak zobrazení, která obsahují <xref:System.Windows.Automation.AutomationElement> pouze objekty relevantní pro konkrétního klienta. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tento přístup umožňuje klientům přizpůsobit strukturu prezentovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podle jejich konkrétních potřeb.  
  
 Klient nástroje má dva způsoby přizpůsobení zobrazení: podle oboru a filtrováním. Rozsah je definující rozsah zobrazení od základního prvku: aplikace může například chtít najít pouze přímé podřízené položky plochy nebo všechny následníky okna aplikace. Filtrování definuje typy prvků, které mají být zahrnuty do zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování definováním vlastností u elementů <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> , <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> včetně vlastností a.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje tři výchozí zobrazení. Tato zobrazení jsou definována typem filtrování provedeno; Rozsah libovolného zobrazení je definován aplikací. Kromě toho může aplikace použít další filtry na vlastnosti; například pro zahrnutí pouze povolených ovládacích prvků do zobrazení ovládacích prvků.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Nezpracované zobrazení  
 Nezpracované zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je úplný <xref:System.Windows.Automation.AutomationElement> strom objektů, pro které je plocha kořenem. Nezpracované zobrazení přesně sleduje nativní programovou strukturu aplikace, a proto je nejpřesnější zobrazení k dispozici. Je to také základ, na kterém jsou sestavena další zobrazení stromu. Vzhledem k tomu, že toto zobrazení [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] závisí na základní architektuře, nezpracovaná zobrazení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítka budou mít [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] jiné nezpracované zobrazení než tlačítko.  
  
 Nezpracované zobrazení se získá tak, že vyhledá prvky bez zadání vlastností nebo pomocí <xref:System.Windows.Automation.TreeWalker.RawViewWalker> pro procházení stromové struktury.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Zobrazení ovládacích prvků  
 Zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacích prvků stromu zjednodušuje úlohu produktu asistenční technologie, která [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] popisuje koncovému uživateli a pomáhá tomuto koncovému uživateli interakci s aplikací, protože [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se úzce mapuje na strukturu. vnímané koncovým uživatelem.  
  
 Zobrazení ovládacího prvku je podmnožinou nezpracovaného zobrazení. Obsahuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracovaného zobrazení, které by koncový uživatel rozuměl jako interaktivní nebo přispívá k logické struktuře ovládacího prvku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]v. Příklady položek, které přispívají k logické struktuře [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nejsou interaktivní, jsou kontejnery položek, jako jsou například záhlaví zobrazení seznamu, panely nástrojů, nabídky a stavový řádek. [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Neinteraktivní položky použité jednoduše pro rozložení nebo dekorativní účely nebudou zobrazeny v zobrazení ovládacího prvku. Příkladem může být panel, který byl použit pouze k rozložení ovládacích prvků v dialogovém okně, ale neobsahuje žádné informace. Neinteraktivní položky, které se zobrazí v zobrazení ovládacího prvku, jsou grafika s informacemi a statický text v dialogovém okně. Neinteraktivní položky, které jsou součástí zobrazení ovládacího prvku, nemohou přijímat fokus klávesnice.  
  
 Zobrazení ovládacího prvku je získáno hledáním prvků, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost nastavenou `true`na nebo pomocí <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> pro procházení stromové struktury.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu je podmnožinou zobrazení ovládacího prvku. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které vyjadřují skutečné informace v uživatelském rozhraní, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, které mohou přijímat fokus klávesnice a textu, který není popiskem na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položce. Například hodnoty v rozevíracím seznamu se zobrazí v zobrazení obsahu, protože představují informace používané koncovým uživatelem. V zobrazení obsahu se pole se seznamem a seznam vystupují jako kolekce [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, kde jedna nebo možná více než jedna položka může být vybrána. Fakt, že jeden je vždy otevřený a jeden může rozbalit a sbalit, je v zobrazení obsahu nepodstatný, protože je navržený tak, aby zobrazoval data nebo obsah, který je prezentován uživateli.  
  
 Zobrazení obsahu je získáno vyhledáním prvků, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost nastavenou `true`na nebo pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> pro procházení stromové struktury.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.AutomationElement>
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
