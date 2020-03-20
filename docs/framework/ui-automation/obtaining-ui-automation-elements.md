---
title: Získání elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: eab4e59ee219808a4c0ae9ca5331a14928b66b5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180001"
---
# <a name="obtaining-ui-automation-elements"></a>Získání elementů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma popisuje různé <xref:System.Windows.Automation.AutomationElement> způsoby [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] získávání objektů pro prvky.  
  
> [!CAUTION]
> Pokud se klientská aplikace může pokusit najít prvky ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastním uživatelském rozhraní, je nutné provést všechna volání v samostatném vlákně. Další informace naleznete v [tématu Problémy s automatizací procesů v uživatelském rozhraní](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Kořenový prvek  
 Všechna hledání <xref:System.Windows.Automation.AutomationElement> objektů musí mít počáteční místo. Může se jedná o libovolný prvek, včetně plochy, okna aplikace nebo ovládacího prvku.  
  
 Kořenový prvek plochy, ze kterého jsou všechny prvky sestoupeny, se získá ze statické <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> vlastnosti.  
  
> [!CAUTION]
> Obecně platí, že byste se měli <xref:System.Windows.Automation.AutomationElement.RootElement%2A>pokusit získat pouze přímé děti . Hledání potomků může iteratprostředi stovky nebo dokonce tisíce prvků, což může mít za následek přetečení zásobníku. Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste začít hledat z okna aplikace nebo z kontejneru na nižší úrovni.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Podmínky  
 Pro většinu technik, které [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] můžete použít k <xref:System.Windows.Automation.Condition>načtení prvků, je nutné zadat soubor , což je sada kritérií definujících, jaké prvky chcete načíst.  
  
 Nejjednodušší podmínkou <xref:System.Windows.Automation.Condition.TrueCondition>je předdefinovaný objekt určující, že mají být vráceny všechny prvky v rámci oboru hledání. <xref:System.Windows.Automation.Condition.FalseCondition>, je <xref:System.Windows.Automation.Condition.TrueCondition>opak , méně užitečný, protože by zabránil nalezení jakýchkoli prvků.  
  
 Tři další předdefinované podmínky lze použít samostatně nebo <xref:System.Windows.Automation.Automation.ContentViewCondition> <xref:System.Windows.Automation.Automation.ControlViewCondition>v <xref:System.Windows.Automation.Automation.RawViewCondition>kombinaci s jinými podmínkami: , , a . <xref:System.Windows.Automation.Automation.RawViewCondition>, který se používá <xref:System.Windows.Automation.Condition.TrueCondition>sám o sobě, je <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> ekvivalentní <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> , protože nefiltruje prvky podle jejich vlastností.  
  
 Další podmínky jsou vytvořeny z <xref:System.Windows.Automation.PropertyCondition> jednoho nebo více objektů, z nichž každý určuje hodnotu vlastnosti. <xref:System.Windows.Automation.PropertyCondition> Může například určit, že prvek je povolen nebo že podporuje určitý vzor ovládacího prvku.  
  
 Podmínky lze kombinovat pomocí logické logiky vytvořením <xref:System.Windows.Automation.AndCondition> <xref:System.Windows.Automation.OrCondition>objektů <xref:System.Windows.Automation.NotCondition>typů , a .  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Obor hledání  
 Vyhledávání provedená <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A> nebo musí mít rozsah, stejně jako výchozí místo.  
  
 Obor definuje prostor kolem místa zahájení, které má být prohledáno. To může zahrnovat samotný prvek, jeho sourozenci, jeho nadřazený, jeho předkové, jeho bezprostřední podřízené objekty a jeho potomci.  
  
 Rozsah hledání je definován bitovou kombinací hodnot z <xref:System.Windows.Automation.TreeScope> výčtu.  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Nalezení známého prvku  
 Chcete-li najít známý prvek, identifikovaný jeho <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, nebo některé jiné vlastnosti <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo kombinace vlastností, je nejjednodušší použít metodu. Pokud je hledaný prvek okno aplikace, počátečním bodem <xref:System.Windows.Automation.AutomationElement.RootElement%2A>hledání může být .  
  
 Tento způsob [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hledání prvků je nejužitečnější ve scénářích automatizovaného testování.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Hledání prvků v podstromu  
 Chcete-li najít všechny prvky splňující určitá kritéria, která souvisejí se známým prvkem, můžete použít <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Tuto metodu můžete například použít k načtení položek seznamu nebo položek nabídky ze seznamu nebo nabídky nebo k identifikaci všech ovládacích prvků v dialogovém okně.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Chůze podstrom  
 Pokud nemáte žádné předchozí znalosti o aplikacích, které váš klient může být použit s, <xref:System.Windows.Automation.TreeWalker> můžete vytvořit podstrom všech prvků zájmu pomocí třídy. Aplikace to může provést v reakci na událost změněné fokusem; To znamená, že když aplikace nebo ovládací prvek obdrží vstupní fokus, klient automatizace uživatelského rozhraní zkoumá podřízené objekty a možná všechny potomky prvku cíle.  
  
 Dalším způsobem, <xref:System.Windows.Automation.TreeWalker> ve kterém lze použít, je identifikovat předchůdce prvku. Například při chůzi do stromu můžete identifikovat nadřazené okno ovládacího prvku.  
  
 Můžete použít <xref:System.Windows.Automation.TreeWalker> buď vytvořením objektu třídy (definování prvků zájmu <xref:System.Windows.Automation.Condition>předáním ) nebo pomocí jednoho z následujících <xref:System.Windows.Automation.TreeWalker>předdefinovaných objektů, které jsou definovány jako pole .  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Vyhledá pouze <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> prvky, jejichž vlastnost je `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Vyhledá pouze <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> prvky, jejichž vlastnost je `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Vyhledá všechny prvky.|  
  
 Poté, co <xref:System.Windows.Automation.TreeWalker>jste získali , jeho použití je jednoduché. Jednoduše volat `Get` metody pro navigaci mezi prvky podstromu.  
  
 Metodu <xref:System.Windows.Automation.TreeWalker.Normalize%2A> lze použít pro navigaci k prvku v podstromu z jiného prvku, který není součástí zobrazení. Předpokládejme například, že jste vytvořili zobrazení <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>podstromu pomocí . Aplikace pak obdrží oznámení, že posuvník obdržel vstupní fokus. Vzhledem k tomu, že posuvník není prvkem obsahu, není k dispozici v zobrazení podstromu. Můžete však předat <xref:System.Windows.Automation.AutomationElement> představující posuvník a načíst <xref:System.Windows.Automation.TreeWalker.Normalize%2A> nejbližší předchůdce, který je v zobrazení obsahu.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Další způsoby načtení prvku  
 Kromě vyhledávání a navigace, můžete načíst <xref:System.Windows.Automation.AutomationElement> následujícízpůsoby.  
  
### <a name="from-an-event"></a>Z události  
 Když aplikace obdrží [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost, zdrojový objekt předaný obslužné rutině <xref:System.Windows.Automation.AutomationElement>události je . Například pokud jste se přihlásili k odběru události změněné fokus, zdroj předán vaše <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> je prvek, který obdržel fokus.  
  
 Další informace naleznete [v tématu Subscribe to UI Automation Events](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z bodu  
 Pokud máte souřadnice obrazovky (například pozici kurzoru), můžete načíst <xref:System.Windows.Automation.AutomationElement> pomocí statické <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metody.  
  
### <a name="from-a-window-handle"></a>Z úchytu okna  
 Chcete-li <xref:System.Windows.Automation.AutomationElement> načíst z HWND, použijte statickou <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metodu.  
  
### <a name="from-the-focused-control"></a>Z cíleného řízení  
 Můžete načíst, <xref:System.Windows.Automation.AutomationElement> který představuje soustředěný <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> ovládací prvek ze statické vlastnosti.  
  
## <a name="see-also"></a>Viz také

- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
