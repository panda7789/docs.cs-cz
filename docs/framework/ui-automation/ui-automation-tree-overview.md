---
title: Přehled stromu automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a88822d6aed5af04ecf7deffe6936cfc4ebe296e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225947"
---
# <a name="ui-automation-tree-overview"></a>Přehled stromu automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Produkty technologií usnadnění a testovací skripty přejděte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu ke shromažďování informací o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a jeho elementy.  
  
 V rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je kořenový prvek stromu existuje (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>), který představuje aktuální plochy a jejíž podřízené elementy reprezentují aplikace pro windows. Každý z těchto podřízených elementů může obsahovat prvky představující kusů [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jako jsou nabídky, tlačítka, panely nástrojů a pole se seznamem. Tyto elementy pak může obsahovat prvky, jako jsou položky seznamu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom není pevný struktury a zřídka dochází v jeho souhrnem vzhledem k tomu může obsahovat tisíce prvky. Součástí jsou vytvořeny a nejsou potřeba, můžete ke změnám, jak přidat, přesunout nebo odebrat prvky.  
  
 Podpora zprostředkovatelů automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu implementací navigace mezi položkami v rámci fragment, který se skládá z kořenového adresáře (obvykle hostované v okně) a podstrom. Poskytovatelé však nejsou obeznámeni s navigace z jednoho ovládacího prvku do jiného. Spravuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jádro, pomocí informací z výchozí okno poskytovatele.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Zobrazení stromu automatizace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Stromu, dají se filtrovat vytvořit zobrazení, které obsahují pouze ty <xref:System.Windows.Automation.AutomationElement> objekty, které jsou relevantní pro konkrétního klienta. Tento přístup umožňuje klientům přizpůsobit struktura prezentovaná prostřednictvím [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] svých konkrétních potřeb.  
  
 Klient má dva způsoby přizpůsobení zobrazení: podle rozsahu a filtrování. Vytváření oboru je definování rozsahu zobrazení, od base element: aplikace může třeba najít pouze přímé podřízené objekty plochy, nebo všechny následníky okna aplikace. Filtrování je definování typů prvků, které mají být zahrnuty do zobrazení.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní podporují filtrování podle definování vlastností prvků, včetně <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> a <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> vlastnosti.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytuje tři výchozí zobrazení. Tato zobrazení jsou definovány typem filtrování provést; obor všechna zobrazení je definované aplikací. Kromě toho aplikace můžete použít další filtry podle vlastnosti; například obsahovat pouze povolené ovládacích prvků v ovládacím zobrazení.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Nezpracované zobrazení  
 Nezpracované zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu je úplný strom <xref:System.Windows.Automation.AutomationElement> objekty, pro které je kořenový adresář. Nezpracované zobrazení přesně dodržuje nativní programový struktury aplikace a tedy nejpodrobnější zobrazení k dispozici. Je také základ, na kterém jsou vytvořeny zobrazení stromu. Protože toto zobrazení závisí na základní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] rozhraní framework, nezpracovaným zobrazením [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] tlačítko bude mít jiné nezpracované zobrazení než [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tlačítko.  
  
 Nezpracované zobrazení se získá tak, že prvky bez zadání vlastnosti nebo pomocí <xref:System.Windows.Automation.TreeWalker.RawViewWalker> přejdete strom.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Ovládací prvek zobrazení  
 Přehled ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu zjednodušuje úlohu produktu technologie pro usnadnění popisující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] pro koncové uživatele a pomáhá tento koncový uživatel interakci s aplikací, protože úzce mapuje na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktura vnímané koncovým uživatelem.  
  
 Ovládací prvek zobrazení je podmnožinou nezpracované zobrazení. Obsahuje všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky z nezpracované zobrazení, které koncový uživatel by pochopit jako interaktivní nebo přispívající k logické struktury ovládacího prvku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Příklady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které přispívají k logické struktury [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ale nejsou interaktivní sami, jsou kontejnery položky jako je například záhlaví zobrazení seznamu, panely nástrojů, nabídky a stavový řádek. Neinteraktivní položky, které používají pouze pro účely dekorativní nebo rozložení se projeví v zobrazení pro ovládací prvek. Příkladem je panel, který byl použit pouze pro vykreslení ovládacích prvků v dialogovém okně, ale sám není neobsahuje žádné informace. Neinteraktivní položky, které se zobrazí v zobrazení ovládání jsou grafika informace a statický text v dialogovém okně. Neinteraktivní položky, které jsou zahrnuty v zobrazení pro ovládací prvek nemůže získat fokus klávesnice.  
  
 Ovládací prvek zobrazení se získá tak, že prvky, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost nastavena na hodnotu `true`, nebo pomocí <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> přejdete strom.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Zobrazení obsahu  
 Zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je podmnožinou ovládacím zobrazení stromu. Obsahuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které true informace v uživatelském rozhraní, včetně [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které můžou přijímat klávesnice fokus a nějaký text, který není v popisku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky. Například hodnoty v rozevíracím seznamem se zobrazí v zobrazení obsahu, které představují informace používá koncový uživatel. V zobrazení obsahu pole se seznamem a pole se seznamem jsou obě reprezentovány ve formě sady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] položky, které je možné vybrat jeden, nebo možná více než jednu položku. Skutečnost, že jeden je vždy otevřít a jeden můžete rozbalit nebo sbalit je bezvýznamná v zobrazení obsahu, protože slouží k zobrazení dat nebo obsahu, který je se budou zobrazovat uživateli.  
  
 Zobrazení obsahu se získá tak, že prvky, které mají <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost nastavena na hodnotu `true`, nebo pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> přejdete strom.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.AutomationElement>
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
