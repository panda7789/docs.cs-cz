---
title: Přehled stromu automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a0b888e8ecc80e3739c583931a86da3cdb7242d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179450"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Produkty asistenční technologie a testovací skripty procházet [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] shromažďovat informace o a jeho prvky.  
  
 Ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je kořenový<xref:System.Windows.Automation.AutomationElement.RootElement%2A>prvek ( ), který představuje aktuální plochu a jehož podřízené prvky představují okna aplikace. Každý z těchto podřízených prvků [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] může obsahovat prvky představující části, jako jsou nabídky, tlačítka, panely nástrojů a seznamy. Tyto prvky zase může obsahovat prvky, jako je například položky seznamu.  
  
 Strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] není pevná struktura a je zřídka vidět v jeho souhrnu, protože může obsahovat tisíce prvků. Jeho části jsou sestaveny podle potřeby a mohou projít změnami při přidávání, přesouvání nebo odebírání prvků.  
  
 Zprostředkovatelé automatizace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uživatelského rozhraní podporují strom implementací navigace mezi položkami v rámci fragmentu, který se skládá z kořenového adresáře (obvykle hostovaného v okně) a podstromu. Zprostředkovatelé se však nezabývají navigací z jednoho ovládacího prvku do druhého. To je spravováno jádrem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pomocí informací od výchozích poskytovatelů oken.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Pohledy na strom automatizace  
 Strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lze filtrovat k vytvoření zobrazení, <xref:System.Windows.Automation.AutomationElement> které obsahují pouze ty objekty relevantní pro konkrétního klienta. Tento přístup umožňuje klientům přizpůsobit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturu prezentované prostřednictvím jejich konkrétních potřeb.  
  
 Klient má dva způsoby přizpůsobení zobrazení: obora a filtrování. Obor je definování rozsahu zobrazení, počínaje základní prvek: například aplikace může chtít najít pouze přímé podřízené plochy nebo všechny potomky okna aplikace. Filtrování definuje typy prvků, které mají být zahrnuty do zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování definováním vlastností na prvky, včetně vlastností <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> a. <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]poskytuje tři výchozí zobrazení. Tato zobrazení jsou definována typem filtrování; rozsah libovolného zobrazení je definován aplikací. Kromě toho aplikace může použít jiné filtry na vlastnosti; chcete-li například zahrnout do zobrazení ovládacího prvku pouze povolené ovládací prvky.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Nezpracovaná zobrazení  
 Nezpracované zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je úplný <xref:System.Windows.Automation.AutomationElement> strom objektů, pro které je plocha kořenem. Nezpracované zobrazení pozorně sleduje nativní programovou strukturu aplikace a proto je nejpodrobnější zobrazení k dispozici. Je to také základna, na které jsou postaveny ostatní pohledy na strom. Vzhledem k tomu, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] že toto zobrazení [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] závisí na podkladovém rozhraní, nebude mít nezpracované zobrazení tlačítka jiné nezpracované zobrazení než tlačítko Win32.  
  
 Nezpracované zobrazení je získáno vyhledáním prvků bez <xref:System.Windows.Automation.TreeWalker.RawViewWalker> zadání vlastností nebo použitím příkazu k navigaci ve stromu.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Zobrazení ovládacího prvku  
 Zobrazení ovládacího [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvku stromu zjednodušuje úkol produktu asistenční technologie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] popisovat koncovému uživateli a pomáhá koncovému uživateli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] komunikovat s aplikací, protože se úzce mapuje na strukturu vnímanou koncovým uživatelem.  
  
 Zobrazení ovládacího prvku je podmnožinou nezpracovaného zobrazení. Zahrnuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracovaného zobrazení, které by koncový uživatel chápal jako [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]interaktivní nebo přispívající k logické struktuře ovládacího prvku v rozhraní . Příklady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položek, které přispívají k [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]logické struktuře , ale nejsou samy o sobě interaktivní, jsou kontejnery položek, jako jsou záhlaví zobrazení seznamu, panely nástrojů, nabídky a stavový řádek. Neinteraktivní položky používané pouze pro rozvržení nebo dekorativní účely nebudou v ovládacím zobrazení vidět. Příkladem je panel, který byl použit pouze k rozložení ovládacích prvků v dialogovém okně, ale sám o sobě neobsahuje žádné informace. Neinteraktivní položky, které budou zobrazeny v ovládacím zobrazení, jsou grafika s informacemi a statický text v dialogu. Neinteraktivní položky, které jsou součástí ovládacího zobrazení, nemohou přijímat fokus klávesnice.  
  
 Zobrazení ovládacího prvku je získáno <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vyhledáním `true`prvků, které <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> mají vlastnost nastavenou na , nebo pomocí procházení stromu.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je podmnožinou zobrazení ovládacího prvku. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které vyjadřují skutečné informace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] v uživatelském rozhraní, včetně položek, které mohou [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] přijímat fokus klávesnice a některý text, který není popisek na položku. Například hodnoty v rozevíracím poli se seznamem se zobrazí v zobrazení obsahu, protože představují informace používané koncovým uživatelem. V zobrazení obsahu jsou pole se seznamem i seznam [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] reprezentovány jako kolekce položek, kde lze vybrat jednu nebo možná více položek. Skutečnost, že jeden je vždy otevřený a jeden může rozbalit a sbalit, je irelevantní v zobrazení obsahu, protože je navržen tak, aby zobrazit data, nebo obsah, který je prezentován uživateli.  
  
 Zobrazení obsahu je získáno vyhledáním <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> prvků, `true`které mají vlastnost <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> nastavenou na , nebo pomocí procházení stromu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.AutomationElement>
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
