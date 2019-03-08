---
title: Získání elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 24a9c63b8d52ef05c386e5bfefe81e33245ece91
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674481"
---
# <a name="obtaining-ui-automation-elements"></a>Získání elementů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje různé způsoby, jak se dá získat <xref:System.Windows.Automation.AutomationElement> objekty pro [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy.  
  
> [!CAUTION]
>  Pokud vaše klientská aplikace může pokusí vyhledat prvky ve své vlastní uživatelské rozhraní, musíte udělat všechny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volá na samostatném vlákně. Další informace najdete v tématu [problémy dělení na vlákna uživatelského rozhraní automatizace](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kořenový Element  
 Všechna vyhledávání <xref:System.Windows.Automation.AutomationElement> objekty musí mít počáteční místě. To může být libovolný element, včetně plochy, okna aplikace nebo ovládacího prvku.  
  
 Kořenový element pro stolní počítače, ze kterého jsou všechny prvky umístění, se získávají z statické <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> vlastnost.  
  
> [!CAUTION]
>  Obecně platí, pokuste se získat jen přímé podřízené objekty daného <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Vyhledání potomků může iterovat stovky nebo i tisíce elementů, což může vést k přetečení zásobníku. Pokud se pokoušíte získat konkrétní elementu na nižší úrovni, měli byste začít hledání v okně aplikace nebo z kontejneru na nižší úrovni.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Podmínky  
 Pro většinu techniky slouží k načtení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvků, je nutné zadat <xref:System.Windows.Automation.Condition>, což je sada kritérií definování jaké prvky, které chcete načíst.  
  
 Nejjednodušší podmínka je <xref:System.Windows.Automation.Condition.TrueCondition>, předdefinovaný objekt určující, zda mají být vráceny všechny prvky v rámci rozsahu vyhledávání. <xref:System.Windows.Automation.Condition.FalseCondition>, první z <xref:System.Windows.Automation.Condition.TrueCondition>, je méně vhodné, protože to by jinak znemožňovaly všechny prvky z jsou zjištěny.  
  
 Tři předdefinované podmínky můžete použít samostatně nebo v kombinaci s další podmínky: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, a <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, použitý samostatně, je ekvivalentní <xref:System.Windows.Automation.Condition.TrueCondition>, protože nefiltruje elementy podle jejich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> nebo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnosti.  
  
 Další podmínky jsou sestaveny z jedné nebo více <xref:System.Windows.Automation.PropertyCondition> objektů, z nichž každý Určuje hodnotu vlastnosti. Například <xref:System.Windows.Automation.PropertyCondition> může určit, že je povoleno elementu nebo že podporuje určité vzoru ovládacích prvků.  
  
 Podmínky lze kombinovat pomocí logické tak, že vytváří objekty typů <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, a <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Obor vyhledávání  
 Vyhledávání pomocí provádí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> musí mít v oboru, jakož i od místa.  
  
 Obor definuje prostor kolem spuštění místní, který má být prohledán. To může zahrnovat elementu samotného, na stejné úrovni, svého nadřazeného objektu, jeho předchůdce, její přímé podřízené objekty a jejích potomků.  
  
 Bitová kombinace hodnot z je definován obor hledání <xref:System.Windows.Automation.TreeScope> výčtu.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Hledání známých Element  
 K vyhledání známý prvek identifikován jeho <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, nebo některé jiné vlastnosti nebo kombinaci těchto vlastností je nejjednodušší použití <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> metoda. Pokud je element žádá o okně aplikace, může být výchozího bodu hledání <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Tímto způsobem hledání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementů je nejužitečnější v automatizovaných testovacích scénářů.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Hledání elementů v podstrom  
 Pokud chcete najít všechny prvky schůzky určitá kritéria, které se týkají známý prvek, můžete použít <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Například můžete použít tuto metodu pro načtení seznamu položky nebo položek nabídky ze seznamu nebo v nabídce, nebo k identifikaci všech ovládacích prvků v dialogovém okně.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Procházení podstrom  
 Pokud nemáte žádné předchozí znalosti, které váš klient může být použit s aplikací, musíte postavit podstrom všechny prvky pomocí <xref:System.Windows.Automation.TreeWalker> třídy. Vaše aplikace se může provést v reakci na událost změnit fokus; To znamená když aplikace nebo ovládacího prvku nastaven vstupní fokus, automatizace uživatelského rozhraní klienta prozkoumá děti a možná všechny následníky elementu zaměřené.  
  
 Jiný způsob, jakým <xref:System.Windows.Automation.TreeWalker> je možné identifikovat předchůdce prvku. Například můžete procházením směrem nahoru identifikovat nadřazené okno ovládacího prvku.  
  
 Můžete použít <xref:System.Windows.Automation.TreeWalker> buď tak, že vytvoříte objekt třídy (definováním prvků, které vás zajímají předáním <xref:System.Windows.Automation.Condition>), nebo pomocí jedné z těchto předdefinovaných objektů, které se definují jako pole <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Vyhledá pouze elementy jehož <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Vyhledá pouze elementy jehož <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Vyhledá všechny elementy.|  
  
 Po získání <xref:System.Windows.Automation.TreeWalker>, jeho použití je jednoduché. Jednoduše zavoláte `Get` metody k navigaci mezi elementy podstrom.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Metodu lze použít pro přechod na prvek v připojeném podstromu z jiného elementu, který není součástí zobrazení. Předpokládejme například, že vytvoříte zobrazení podstrom pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Aplikace pak obdrží oznámení, že posuvník přijal zaměření pro vstup. Vzhledem k tomu, že posuvník není content element, není k dispozici v zobrazení podstrom. Můžete však předat <xref:System.Windows.Automation.AutomationElement> představující posuvník pro <xref:System.Windows.Automation.TreeWalker.Normalize%2A> a načíst nejbližším podřízeném objektu, který je v zobrazení obsahu.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Další možnosti, jak načíst prvek  
 Kromě hledání a navigaci, můžete načíst <xref:System.Windows.Automation.AutomationElement> následujícími způsoby.  
  
### <a name="from-an-event"></a>Z události  
 Když aplikace obdrží [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí, je zdrojový objekt předaný obslužné rutině události <xref:System.Windows.Automation.AutomationElement>. Například pokud se přihlášení k odběru události změny fokus, zdroj předán vaší <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> je prvek, který přijal fokus.  
  
 Další informace najdete v tématu [přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z bodu  
 Pokud máte souřadnice obrazovky (například pozice kurzoru), můžete načíst <xref:System.Windows.Automation.AutomationElement> pomocí statické <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metody.  
  
### <a name="from-a-window-handle"></a>Z popisovač okna  
 K načtení <xref:System.Windows.Automation.AutomationElement> od HWND, použít statické <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metody.  
  
### <a name="from-the-focused-control"></a>Z ovládacího prvku fokusem  
 Můžete načíst <xref:System.Windows.Automation.AutomationElement> cílené ovládací prvek, který představuje ze statické <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:
- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
