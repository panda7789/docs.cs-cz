---
title: Práce s mezipamětí u klientů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: fa96a12c92703430482b765d625067fbf08c3477
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410309"
---
# <a name="caching-in-ui-automation-clients"></a>Práce s mezipamětí u klientů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje ukládání do mezipaměti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti a řízení vzory.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ukládání do mezipaměti znamená předem načítání dat. Data lze přistupovat bez další komunikace mezi procesy. Ukládání do mezipaměti se obvykle používá v klientských aplikacích automatizace uživatelského rozhraní pro načtení vlastnosti a vzory ovládacích prvků hromadně. Je pak načíst informace z mezipaměti podle potřeby. Aplikace aktualizace mezipaměti pravidelně, obvykle v reakci na události což svědčí o tom to něco v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] došlo ke změně.  
  
 Výhody ukládání do mezipaměti, jsou nejvíce patrné s Windows Presentation Foundation (WPF) a vlastních ovládacích prvků, které mají zprostředkovatele automatizace uživatelského rozhraní na straně serveru. Při přístupu k zprostředkovatele na straně klienta jako je například výchozí zprostředkovatele pro menší výhoda je [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládací prvky.  
  
 Ukládání do mezipaměti nastane, když se aktivuje aplikaci <xref:System.Windows.Automation.CacheRequest> a pak používá žádné metody nebo vlastnosti, která vrací <xref:System.Windows.Automation.AutomationElement>, například <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody <xref:System.Windows.Automation.TreeWalker> třídy jsou výjimku; ukládání do mezipaměti je možné pouze pokud <xref:System.Windows.Automation.CacheRequest> je zadána jako parametr (například <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Ukládání do mezipaměti také nastane, když se přihlásíte k události při <xref:System.Windows.Automation.CacheRequest> je aktivní. <xref:System.Windows.Automation.AutomationElement> Předaný vaší obslužné rutiny události podle zdroje události obsahuje vlastnosti uloženou v mezipaměti a vzory určeného původní <xref:System.Windows.Automation.CacheRequest>. Některé změny provedené <xref:System.Windows.Automation.CacheRequest> po přihlášení k odběru události nemají žádný vliv.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnosti a řízení vzory elementu můžete uložit do mezipaměti.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Možnosti pro ukládání do mezipaměti  
 <xref:System.Windows.Automation.CacheRequest> Určuje následující možnosti pro ukládání do mezipaměti.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Vlastnosti do mezipaměti  
 Můžete zadat vlastnosti do mezipaměti voláním <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> pro každou vlastnost před aktivací žádosti.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Vzory ovládacích prvků do mezipaměti  
 Vzory ovládacích prvků do mezipaměti můžete zadat při volání <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> pro každý vzor před aktivací žádosti. Pokud je vzor uložené v mezipaměti, jeho vlastnosti se neukládají do mezipaměti automaticky; musíte zadat vlastnosti, které má v mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Obor a filtrování ukládání do mezipaměti  
 Elementy můžete určit, jehož vlastnosti a vzorů, které chcete do mezipaměti, a to nastavením <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> vlastnost před aktivací žádosti. Rozsah je relativní vzhledem k prvky, které se načítají, když je aktivní žádosti. Například pokud nastavíte pouze <xref:System.Windows.Automation.TreeScope.Children>a následně načíst <xref:System.Windows.Automation.AutomationElement>, vlastnosti a vzory podřízené objekty tohoto elementu jsou uložené v mezipaměti, ale u elementu samotného. Chcete-li zajistit, aby ukládání do mezipaměti pro načtený elementu samotného, je nutné zahrnout <xref:System.Windows.Automation.TreeScope.Element> v <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnost. Není možné nastavit obor <xref:System.Windows.Automation.TreeScope.Parent> nebo <xref:System.Windows.Automation.TreeScope.Ancestors>. Ale nadřazený element můžete uložit do mezipaměti, pokud je podřízený element uložené v mezipaměti; v tomto tématu najdete v části načítání podřízené objekty do mezipaměti a nadřazené položky.  
  
 Také obsahuje rozsah ukládání do mezipaměti <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> vlastnost. Ve výchozím nastavení, ukládání do mezipaměti se provádí pouze u elementů, které se zobrazují v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Můžete však změnit tuto vlastnost použít ukládání do mezipaměti pro všechny elementy nebo pouze pro elementy, které se zobrazují v zobrazení obsahu.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Sílu odkazy – Element  
 Pokud načítáte <xref:System.Windows.Automation.AutomationElement>, ve výchozím nastavení mají přístup ke všem vlastnosti a vzory tohoto elementu, včetně těch, které nebyly uloženy v mezipaměti. Však pro vyšší efektivity můžete zadat, že odkaz na element odkazuje data uložená v mezipaměti pouze podle nastavení <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost <xref:System.Windows.Automation.CacheRequest> k <xref:System.Windows.Automation.AutomationElementMode.None>. V takovém případě nemáte přístup k žádné vlastnosti bez mezipaměti a vzory načtené elementů. To znamená, že všechny vlastnosti prostřednictvím nelze získat přístup <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo `Current` vlastnost <xref:System.Windows.Automation.AutomationElement> nebo všechny – vzor ovládacích prvků; ani můžete načíst vzor pomocí <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. V mezipaměti vzory, můžete volat metody, které se načíst vlastnosti pole, jako například <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale ne všechny, které provádějí akce na ovládací prvek, jako například <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Je například aplikace, která nemusí úplné odkazy na objekty z obrazovky, který by předběžné načtení <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> a <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastnosti elementů v okně, ale nebude potřeba <xref:System.Windows.Automation.AutomationElement> samotných objektech.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktivace Vlastnost CacheRequest  
 Ukládání do mezipaměti se provádí pouze tehdy, když <xref:System.Windows.Automation.AutomationElement> objekty jsou načteny při <xref:System.Windows.Automation.CacheRequest> je aktivní pro aktuální vlákno. Existují dva způsoby, jak aktivovat <xref:System.Windows.Automation.CacheRequest>.  
  
 Obvyklým způsobem se má volat <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Tato metoda vrátí objekt, který implementuje <xref:System.IDisposable>. Žádost zůstane aktivní, dokud <xref:System.IDisposable> objekt existuje. Nejjednodušší způsob, jak řídit doba života objektu je uzavřete volání v rámci `using` (C#) nebo `Using` blokování (Visual Basic). Tím se zajistí, že žádost odebrány ze zásobníku, i v případě, že dojde k výjimce.  
  
 Jiným způsobem, což je užitečné, když chcete vnořit požadavků na mezipaměť, je volání <xref:System.Windows.Automation.CacheRequest.Push%2A>. To vloží požadavek na zásobníku a aktivuje jej. Žádost zůstane aktivní, dokud se odebere ze zásobníku podle <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Požadavek stane dočasně neaktivní, pokud jiná žádost je vloženy do zásobníku; pouze nejvyšší žádosti v zásobníku je aktivní.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Načítání vlastností do mezipaměti  
 V mezipaměti vlastnosti elementu můžete načíst pomocí následující metody a vlastnosti.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Pokud požadovaná vlastnost není v mezipaměti, je vyvolána výjimka.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, jako je <xref:System.Windows.Automation.AutomationElement.Current%2A>, zpřístupní jednotlivé vlastnosti jako členové struktury. Však není potřeba načíst tuto strukturu; jednotlivé vlastnosti můžete přistupovat přímo. Například <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> vlastnost lze získat z `element.Cached.Name`, kde `element` je <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Načítání vzorů ovládacích prvků do mezipaměti  
 Vzory v mezipaměti ovládacích prvků elementu můžete načíst pomocí následujících metod.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Pokud vzor není v mezipaměti, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> vyvolá výjimku, a <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> vrátí `false`.  
  
 V mezipaměti vlastnosti vzor ovládacích prvků můžete načíst pomocí `Cached` vlastnost vzor objektu. Můžete také načíst aktuální hodnoty prostřednictvím `Current` vlastnost, ale jenom v případě <xref:System.Windows.Automation.AutomationElementMode.None> nebyla zadána při <xref:System.Windows.Automation.AutomationElement> byla načtena. (<xref:System.Windows.Automation.AutomationElementMode.Full> je výchozí hodnota, a to umožňuje přístup k aktuální hodnoty.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Načítání do mezipaměti, děti a nadřízených prvků  
 Pokud načítáte <xref:System.Windows.Automation.AutomationElement> a ukládání do mezipaměti pro podřízené objekty tohoto elementu prostřednictvím <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnost požadavku, je následně možné získat podřízené elementy z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> vlastnost elementu, který jste získali.  
  
 Pokud <xref:System.Windows.Automation.TreeScope.Element> zahrnutý v oboru požadavku mezipaměti je následně k dispozici z kořenový element požadavku <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> vlastnost žádnou z podřízených elementů.  
  
> [!NOTE]
>  Nelze mezipaměti rodiče nebo nadřazených kořenového prvku požadavku.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizace mezipaměti  
 Mezipaměť je platný pouze tak dlouho, dokud nic změn v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Aplikace je zodpovědná za aktualizace mezipaměti, obvykle v reakci na události.  
  
 Pokud se přihlásíte k události při <xref:System.Windows.Automation.CacheRequest> je získáte aktivní, <xref:System.Windows.Automation.AutomationElement> s aktualizované mezipaměti jako zdroj událostí vždy, když se nazývá vaší obslužné rutiny události delegáta. Můžete také aktualizovat informace uložené v mezipaměti pro element voláním <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Abyste mohli předávat původní <xref:System.Windows.Automation.CacheRequest> aktualizovat všechny informace, které se dříve ukládá do mezipaměti.  
  
 Aktualizace mezipaměti nezmění vlastnosti všechny existující <xref:System.Windows.Automation.AutomationElement> odkazy.  
  
## <a name="see-also"></a>Viz také  
 [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Ukázka FetchTimer](http://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
