---
title: Získání elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 8c222cb2cf70502024a5934c4c527334c9f24165
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966388"
---
# <a name="obtaining-ui-automation-elements"></a>Získání elementů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma popisuje různé způsoby získání <xref:System.Windows.Automation.AutomationElement> objektů pro [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvky.  
  
> [!CAUTION]
>  Pokud se vaše klientská aplikace může pokusit najít prvky ve vlastním uživatelském rozhraní, je nutné provést [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] všechna volání v samostatném vlákně. Další informace najdete v tématu [problémy s vlákny pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kořenový element  
 Všechna hledání <xref:System.Windows.Automation.AutomationElement> objektů musí mít počáteční umístění. Může to být libovolný element, včetně plochy, okna aplikace nebo ovládacího prvku.  
  
 Kořenový element pro plochu, ze kterého jsou pořízené všechny prvky, se získá z vlastnosti static <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> .  
  
> [!CAUTION]
>  Obecně byste se měli pokusit získat pouze přímé podřízené objekty <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Hledání potomků může iterovat stovky nebo dokonce tisíce prvků, což může způsobit přetečení zásobníku. Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste zahájit hledání z okna aplikace nebo z kontejneru na nižší úrovni.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Podmínky  
 Pro většinu technik, které lze použít k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] načtení prvků, je nutné zadat <xref:System.Windows.Automation.Condition>a, což je sada kritérií definujících prvky, které chcete načíst.  
  
 Nejjednodušší podmínka je <xref:System.Windows.Automation.Condition.TrueCondition>, předdefinovaný objekt určující, že všechny prvky v rámci oboru vyhledávání mají být vráceny. <xref:System.Windows.Automation.Condition.FalseCondition>, povýšení <xref:System.Windows.Automation.Condition.TrueCondition>, je méně užitečné, protože by se zabránilo v nalezení nalezených prvků.  
  
 Tři další předdefinované podmínky lze použít samostatně nebo v kombinaci s jinými podmínkami: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>a <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, který používá sám sebe, je ekvivalentní <xref:System.Windows.Automation.Condition.TrueCondition>k, protože nefiltruje prvky podle jejich <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> vlastností <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> nebo.  
  
 Další podmínky jsou vytvořeny z jednoho nebo více <xref:System.Windows.Automation.PropertyCondition> objektů, z nichž každý Určuje hodnotu vlastnosti. Například <xref:System.Windows.Automation.PropertyCondition> může určovat, že prvek je povolen nebo že podporuje určitý vzor ovládacího prvku.  
  
 Podmínky lze kombinovat pomocí logické logiky sestavením objektů typů <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>a <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Obor vyhledávání  
 Hledání se provádí pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> musí mít obor i počáteční umístění.  
  
 Rozsah definuje prostor kolem počátečního místa, které má být prohledáno. To může zahrnovat samotný prvek, jeho členy stejné úrovně, jeho nadřízený, jeho nadřazené prvky, jejich bezprostřední podřízené objekty a její následníky.  
  
 Rozsah hledání je definován bitovou kombinací hodnot z <xref:System.Windows.Automation.TreeScope> výčtu.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Hledání známého prvku  
 Chcete-li najít známý prvek identifikovaný jeho <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>nebo jinou vlastnost nebo kombinaci vlastností, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> je nejjednodušší použít metodu. Pokud je požadovaný prvek oknem aplikace, počáteční bod hledání může být <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Tento způsob hledání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementů je nejužitečnější v případech automatizovaného testování.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Hledání prvků v podstromu  
 Chcete-li najít všechny prvky splňující konkrétní kritéria, která souvisí se známým elementem, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>můžete použít. Například můžete použít tuto metodu pro načtení položek seznamu nebo položek nabídky ze seznamu nebo nabídky nebo pro identifikaci všech ovládacích prvků v dialogovém okně.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Procházení podstromu  
 Pokud nemáte žádné předchozí znalosti o aplikacích, se kterými je možné klienta použít, můžete vytvořit podstrom všech prvků zájmu pomocí <xref:System.Windows.Automation.TreeWalker> třídy. Vaše aplikace to může udělat v reakci na událost změny v rámci fokusu; To znamená, že když aplikace nebo ovládací prvek dostane fokus vstupu, klient automatizace uživatelského rozhraní prověřuje podřízené prvky a případně všechny následníky elementu s fokusem.  
  
 Jiný způsob, <xref:System.Windows.Automation.TreeWalker> jak lze použít, je k identifikaci nadřazených prvků prvku. Například při procházení stromu můžete identifikovat nadřazené okno ovládacího prvku.  
  
 Můžete použít <xref:System.Windows.Automation.TreeWalker> buď vytvořením objektu třídy (definováním elementů zájmu <xref:System.Windows.Automation.Condition>předáním), nebo pomocí jednoho z následujících předdefinovaných objektů, které <xref:System.Windows.Automation.TreeWalker>jsou definovány jako pole.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Vyhledá pouze prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> , jejichž `true`vlastnost je.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Vyhledá pouze prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> , jejichž `true`vlastnost je.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Vyhledá všechny prvky.|  
  
 Po získání <xref:System.Windows.Automation.TreeWalker>je použití jednoduché. Jednoduše zavolejte `Get` metody pro navigaci mezi prvky podstromu.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Metodu lze použít pro přechod na prvek v podstromu z jiného prvku, který není součástí zobrazení. Předpokládejme například, že jste vytvořili zobrazení podstromu pomocí <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Vaše aplikace poté obdrží oznámení o tom, že posuvník obdržel vstupní fokus. Vzhledem k tomu, že posuvník není prvkem obsahu, není k dispozici v zobrazení podstromu. Můžete však předat <xref:System.Windows.Automation.AutomationElement> , aby <xref:System.Windows.Automation.TreeWalker.Normalize%2A> posuvník představoval a načetl nejbližší předchůdce, který je v zobrazení obsahu.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Další způsoby, jak načíst element  
 Kromě vyhledávání a navigace můžete načíst <xref:System.Windows.Automation.AutomationElement> následujícími způsoby.  
  
### <a name="from-an-event"></a>Z události  
 Když aplikace obdrží [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událost, zdrojový objekt předaný obslužné rutině události <xref:System.Windows.Automation.AutomationElement>je. Například pokud jste se přihlásili k odběru událostí změněných fokusu, je zdroj předaný <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> do vašeho prvku, který dostal fokus.  
  
 Další informace najdete v tématu [přihlášení k odběru událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Z bodu  
 Pokud máte souřadnice obrazovky (například pozice kurzoru), můžete načíst <xref:System.Windows.Automation.AutomationElement> pomocí statické <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metody.  
  
### <a name="from-a-window-handle"></a>Z popisovače okna  
 Chcete-li <xref:System.Windows.Automation.AutomationElement> načíst z HWND, použijte statickou <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> metodu.  
  
### <a name="from-the-focused-control"></a>Z ovládacího prvku s fokusem  
 Můžete načíst <xref:System.Windows.Automation.AutomationElement> , který reprezentuje ovládací prvek s fokusem ze statické <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
