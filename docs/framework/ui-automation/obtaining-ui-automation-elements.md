---
title: Získání elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3e700e7e726b5cb71d3b7d863bdb31951aacd885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399199"
---
# <a name="obtaining-ui-automation-elements"></a>Získání elementů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje různé způsoby, kterými se dá získat <xref:System.Windows.Automation.AutomationElement> objekty pro [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementy.  
  
> [!CAUTION]
>  Pokud klientské aplikace může pokus o vyhledání elementy v jeho vlastní uživatelské rozhraní, musíte udělat všechny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání na samostatné vlákno. Další informace najdete v tématu [problémy dělení na vlákna automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kořenový Element  
 Vyhledá všechny <xref:System.Windows.Automation.AutomationElement> objekty musí mít od místní. Může to být libovolný element, včetně plochy, okna aplikace nebo ovládacího prvku.  
  
 Kořenový element pro stolní počítače, ve kterém jsou všechny elementy který, se získávají z statických <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> vlastnost.  
  
> [!CAUTION]
>  Obecně platí, že byste měli zkusit získat jen přímé podřízené objekty daného <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Vyhledejte následníky může iterovat stovky nebo dokonce tisíce elementy, což může způsobit k přetečení zásobníku. Pokud se pokoušíte získat konkrétní element na nižší úrovni, měli byste začít vyhledávání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Podmínky  
 Pro většinu techniky, kterou můžete použít k načtení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy, je nutné zadat <xref:System.Windows.Automation.Condition>, což je sada kritérií definování přizpůsobitelné prvky, které chcete načíst.  
  
 Nejjednodušší podmínka je <xref:System.Windows.Automation.Condition.TrueCondition>, objekt předdefinované určující, zda mají být vráceny všechny elementy v rámci oboru vyhledávání. <xref:System.Windows.Automation.Condition.FalseCondition>, konverzace z <xref:System.Windows.Automation.Condition.TrueCondition>, je méně užitečné, protože ho by bránily všechny elementy jsou zjištěny.  
  
 Tři předem definované podmínky může být použito samostatně nebo v kombinaci s jinými podmínkami: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, a <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, použitý samostatně, je ekvivalentní <xref:System.Windows.Automation.Condition.TrueCondition>, protože nefiltruje elementy podle jejich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> nebo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnosti.  
  
 Další podmínky sestavují z jedné nebo více <xref:System.Windows.Automation.PropertyCondition> objektů, z nichž každý Určuje hodnotu vlastnosti. Například <xref:System.Windows.Automation.PropertyCondition> může určit, že je povoleno element nebo že podporuje určité – vzor ovládacích prvků.  
  
 Podmínky lze spojovat pomocí vytváření objektů typu Boolean logiku <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, a <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Obor vyhledávání  
 Vyhledávání pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> musí mít obor, jakož i spouštění místní.  
  
 Obor definuje prostor kolem spuštění místní, které má být prohledán. To může obsahovat elementu samotného, uzly na stejné úrovni, jeho nadřazený objekt, jeho předchůdců, jeho přímé podřízené objekty a jeho následníky.  
  
 Obor vyhledávání je definována bitovou kombinaci hodnot z <xref:System.Windows.Automation.TreeScope> výčtu.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Hledání známých Element  
 K hledání známých prvku identifikovaný jeho <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, nebo jinou vlastností nebo kombinaci vlastností, je to nejjednodušší provádět používat <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> metoda. Pokud je element žádá o okna aplikace, může být výchozího bodu hledání <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Tímto způsobem hledání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy je velmi užitečné v situacích automatizované testování.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Vyhledávání elementů v podstrom  
 Chcete-li najít všechny elementy schůzku určitá kritéria, které se vztahují k prvku známé, můžete použít <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Můžete například použít tuto metodu můžete načíst položky seznamu nebo položky nabídky ze seznamu nebo nabídky, nebo zjistit všechny ovládací prvky v dialogovém okně.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Proti podstrom  
 Pokud nemáte žádné předchozí znalosti z aplikací, které lze použít s vašeho klienta, můžete vytvořit podstrom všech elementů vás zajímají pomocí <xref:System.Windows.Automation.TreeWalker> třídy. Aplikace se může provést v reakci na událost o změně fokus; To znamená když aplikace nebo ovládací prvek obdrží zaměření pro vstup, prověří automatizace uživatelského rozhraní klienta, děti a případně všech potomků cílených elementu.  
  
 Dalším způsobem, ve kterém <xref:System.Windows.Automation.TreeWalker> lze je identifikovat nadřazených elementu. Můžete například rámci nahoru k identifikovat nadřazené okno ovládacího prvku.  
  
 Můžete použít <xref:System.Windows.Automation.TreeWalker> buď tak, že vytvoříte objekt třídy (definování elementů vás zajímají předáním <xref:System.Windows.Automation.Condition>), nebo pomocí jedné z těchto předdefinovaných objektů, které jsou definovány jako pole <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Vyhledá pouze elementy, jejichž <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> vlastnost je `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Vyhledá pouze elementy, jejichž <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastnost je `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Vyhledá všechny elementy.|  
  
 Po získání <xref:System.Windows.Automation.TreeWalker>, jeho použití je jednoduché. Jednoduše volání `Get` metody pro pohyb mezi elementy podstrom.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Metodu lze použít pro navigaci na element v podstromě z jiný element, který není součástí zobrazení. Předpokládejme například, že jste vytvořili zobrazení podstrom pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Aplikace pak obdrží oznámení, že posuvník přijal zaměření pro vstup. Protože posuvníku není element obsahu, není přítomen v zobrazení podstrom. Však můžete předat <xref:System.Windows.Automation.AutomationElement> představující posuvníku <xref:System.Windows.Automation.TreeWalker.Normalize%2A> a načtení nejbližším podřízeném objektu, který je v zobrazení obsahu.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Další způsoby, jak načíst elementu  
 Kromě hledání a navigace, můžete načíst <xref:System.Windows.Automation.AutomationElement> následujícím způsobem.  
  
### <a name="from-an-event"></a>Z události  
 Pokud vaše aplikace přijímá [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost, je zdrojový objekt předaný vaší obslužné rutiny událostí <xref:System.Windows.Automation.AutomationElement>. Například pokud jste přihlášení k odběru události změny fokus, zdroj předaný vaší <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> je elementu, který fokus.  
  
 Další informace najdete v tématu [přihlásit k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z bodu  
 Pokud máte souřadnice obrazovky (například pozice kurzoru), můžete načíst <xref:System.Windows.Automation.AutomationElement> pomocí statické <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metoda.  
  
### <a name="from-a-window-handle"></a>Z popisovač okna  
 Načtení <xref:System.Windows.Automation.AutomationElement> popisovačem HWND používat statickou <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metoda.  
  
### <a name="from-the-focused-control"></a>Z ovládacího prvku s fokusem  
 Můžete načíst <xref:System.Windows.Automation.AutomationElement> představující cílených ovládací prvek z statických <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
