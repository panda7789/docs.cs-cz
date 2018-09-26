---
title: Práce s mezipamětí u klientů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 2b821a1deb947db86e89207c447045f76a8bb842
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084771"
---
# <a name="caching-in-ui-automation-clients"></a>Práce s mezipamětí u klientů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje ukládání do mezipaměti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory vlastností a ovládacího prvku.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ukládání do mezipaměti znamená předběžného načítání dat. Data lze přistupovat bez další komunikaci mezi procesy. Ukládání do mezipaměti se obvykle používá u automatizace uživatelského rozhraní klientských aplikací k načtení vlastností a vzorů ovládacích prvků hromadně. Informace je pak načten z mezipaměti, podle potřeby. Aplikace aktualizuje mezipaměť pravidelně, obvykle v reakci na události označuje, že něco v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] došlo ke změně.  
  
 Výhody ukládání do mezipaměti jsou nejvíce patrné s Windows Presentation Foundation (WPF) a vlastních ovládacích prvků, které mají zprostředkovatelů automatizace uživatelského rozhraní na straně serveru. Při přístupu k poskytovatele na straně klienta, jako je výchozí poskytovatele pro méně výhoda je [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ovládacích prvků.  
  
 Ukládání do mezipaměti nastane, pokud se aplikace aktivuje <xref:System.Windows.Automation.CacheRequest> a potom pomocí libovolné metody nebo vlastnosti, která vrací <xref:System.Windows.Automation.AutomationElement>; například <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Metody <xref:System.Windows.Automation.TreeWalker> třídy jsou výjimku, ukládání do mezipaměti pouze probíhá-li <xref:System.Windows.Automation.CacheRequest> je zadána jako parametr (například <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Ukládání do mezipaměti také vyvolá se při vytvoření odběru událostí při <xref:System.Windows.Automation.CacheRequest> je aktivní. <xref:System.Windows.Automation.AutomationElement> Předaný obslužné rutině události, zdroj události obsahuje vlastnostem uloženým v mezipaměti a vzorům uvedeným v původní <xref:System.Windows.Automation.CacheRequest>. Všechny změny provedené <xref:System.Windows.Automation.CacheRequest> po přihlášení odběru události nemají žádný vliv.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Mezipaměti vlastností a ovládací prvek vzorů elementu.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Možnosti pro ukládání do mezipaměti  
 <xref:System.Windows.Automation.CacheRequest> Určuje následující možnosti pro ukládání do mezipaměti.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Vlastnosti mezipaměti  
 Můžete zadat vlastnosti mezipaměti voláním <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> pro každou vlastnost před aktivací požadavku.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Vzory ovládacích prvků do mezipaměti  
 Vzory ovládacích prvků do mezipaměti můžete určit pomocí volání <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> pro každý vzorek před aktivací požadavku. Pokud vzor je uložené v mezipaměti, její vlastnosti nejsou uložené v mezipaměti automaticky; je nutné zadat požadované vlastnosti uložené v mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Rozsah a filtrování ukládání do mezipaměti  
 Můžete určit prvky, jehož vlastnosti a vzorce, které chcete uložit do mezipaměti pomocí nastavení <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> vlastnost před aktivací požadavku. Obor je relativní vzhledem k prvky, které se načítají, když je žádost aktivní. Například pokud nastavíte pouze <xref:System.Windows.Automation.TreeScope.Children>a potom získá <xref:System.Windows.Automation.AutomationElement>, vlastnosti a vzorce z podřízených prvků tohoto prvku jsou uložené v mezipaměti, ale u elementu samotného. Aby bylo zajištěno, že ukládání do mezipaměti se automaticky načtena elementu samotného, je nutné zahrnout <xref:System.Windows.Automation.TreeScope.Element> v <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnost. Není možné nastavit rozsah na <xref:System.Windows.Automation.TreeScope.Parent> nebo <xref:System.Windows.Automation.TreeScope.Ancestors>. Ale nadřazený element můžete uložit do mezipaměti, pokud podřízený element se uloží do mezipaměti; v tomto tématu najdete v článku načítání mezipaměti podřízené a nadřazené položky.  
  
 Rozsah ukládání do mezipaměti je také vliv <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> vlastnost. Ve výchozím nastavení, ukládání do mezipaměti se provádí pouze u elementů, které se zobrazují v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Můžete však změnit tuto vlastnost použít, ukládání do mezipaměti na všechny elementy nebo pouze na prvky, které se zobrazují v zobrazení obsahu.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Síla odkazy – Element  
 Při načtení <xref:System.Windows.Automation.AutomationElement>, ve výchozím nastavení mají přístup ke všem vlastnosti a vzorce tohoto prvku, včetně těch, které nebyly uloženy v mezipaměti. Však pro vyšší efektivitu můžete zadat, že odkaz na prvek odkazuje na data uložená v mezipaměti, tak, že nastavíte <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost <xref:System.Windows.Automation.CacheRequest> k <xref:System.Windows.Automation.AutomationElementMode.None>. V takovém případě nemáte přístup k žádné vlastnosti bez mezipaměti a vzory načtených prvků. To znamená, že nelze přistupovat k žádné vlastnosti prostřednictvím <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo `Current` vlastnost <xref:System.Windows.Automation.AutomationElement> nebo jakékoli – vzor ovládacích prvků; ani můžete načíst vzor pomocí <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Na vzory v mezipaměti, můžete volat metody, které načítají vlastnosti pole, jako například <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ale ne všechny, jako například provádět akce na ovládacím prvku <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Příklad aplikace, která nemusí potřebovat úplný odkazy na objekty se čtečkou obrazovky, který by předběžné načtení <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> a <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastnosti elementů v okně, ale nebude potřeba <xref:System.Windows.Automation.AutomationElement> samotných objektech.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Aktivace CacheRequest  
 Ukládání do mezipaměti se provádí jenom v případě <xref:System.Windows.Automation.AutomationElement> objekty jsou načteny během <xref:System.Windows.Automation.CacheRequest> je aktivní pro aktuální vlákno. Existují dva způsoby, jak aktivovat <xref:System.Windows.Automation.CacheRequest>.  
  
 Obvyklým způsobem je volání <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Tato metoda vrátí objekt, který implementuje <xref:System.IDisposable>. Zůstane aktivní, žádosti za předpokladu, <xref:System.IDisposable> objekt existuje. Nejjednodušší způsob, jak řídit dobu života objektu je uzavřete volání v rámci `using` (C#) nebo `Using` blokování (Visual Basic). Tím se zajistí, že žádost bude odebrán ze zásobníku, i v případě, že je vyvolána výjimka.  
  
 Dalším způsobem, což je užitečné, pokud chcete vnořit požadavků mezipaměti, je volání <xref:System.Windows.Automation.CacheRequest.Push%2A>. To umístí požadavek na zásobníku a aktivuje jej. Žádost zůstane aktivní, dokud je odebrán ze zásobníku podle <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Přestane být požadavek dočasně aktivní, pokud jiná žádost je vloženo do zásobníku; pouze horní požadavek v zásobníku je aktivní.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Načítání vlastností do mezipaměti  
 V mezipaměti vlastnosti elementu můžete načíst pomocí následující metody a vlastnosti.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Pokud požadovaná vlastnost není v mezipaměti, je vyvolána výjimka.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, jako je <xref:System.Windows.Automation.AutomationElement.Current%2A>, uvádí jednotlivé vlastnosti jako členy struktury. Ale není potřeba načíst tuto strukturu; jednotlivé vlastnosti můžete přistupovat přímo. Například <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> můžete získat vlastnost `element.Cached.Name`, kde `element` je <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Načítání vzorů ovládacích prvků do mezipaměti  
 Vzory uložené v mezipaměti ovládacího prvku můžete načíst pomocí následujících metod.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Pokud vzor není v mezipaměti, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> vyvolá výjimku, a <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> vrátí `false`.  
  
 V mezipaměti vlastnosti vzor ovládacích prvků můžete načíst pomocí `Cached` vlastnost v objektu modelu. Můžete také načíst aktuální hodnoty prostřednictvím `Current` vlastnost, ale pouze v případě <xref:System.Windows.Automation.AutomationElementMode.None> nebyla zadána při <xref:System.Windows.Automation.AutomationElement> byla načtena. (<xref:System.Windows.Automation.AutomationElementMode.Full> je výchozí hodnota, a to umožňuje přístup k aktuální hodnoty.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Načítání do mezipaměti podřízené a nadřazené položky  
 Při načtení <xref:System.Windows.Automation.AutomationElement> a žádat o ukládání do mezipaměti pro podřízené objekty daného prvku prostřednictvím <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnosti požadavku, je následně nemůže zobrazit podřízené prvky z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> vlastnost elementu, který jste získali.  
  
 Pokud <xref:System.Windows.Automation.TreeScope.Element> byla zahrnuta v oboru požadavku mezipaměti je následně k dispozici z kořenový element požadavku <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> vlastnost některý z podřízených prvků.  
  
> [!NOTE]
>  Nelze mezipaměti nadřazené prvky nebo předchůdce kořenový element požadavku.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Aktualizace mezipaměti  
 Mezipaměť je platný pouze tak dlouho, dokud se nic nemění v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Aplikace je zodpovědný za automatickou aktualizaci mezipaměti, obvykle v reakci na události.  
  
 Je-li přihlásit odběr události při <xref:System.Windows.Automation.CacheRequest> je aktivní, kterou získáte <xref:System.Windows.Automation.AutomationElement> s aktualizovanou mezipaměti jako zdroj události pokaždé, když je volána delegát obslužné rutiny události. Můžete také aktualizovat informace uložené v mezipaměti pro element voláním <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Můžete předat původní <xref:System.Windows.Automation.CacheRequest> aktualizovat všechny informace, které se dříve uložené v mezipaměti.  
  
 Aktualizace mezipaměti nezmění vlastnosti všechny existující <xref:System.Windows.Automation.AutomationElement> odkazy.  
  
## <a name="see-also"></a>Viz také  
 [Události automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Ukázka FetchTimer](https://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
