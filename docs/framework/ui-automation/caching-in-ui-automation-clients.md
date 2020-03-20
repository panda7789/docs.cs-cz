---
title: Práce s mezipamětí u klientů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 186ed77594aadab9e3f49ef30e559e159aee1b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180279"
---
# <a name="caching-in-ui-automation-clients"></a>Práce s mezipamětí u klientů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje ukládání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností do mezipaměti a vzory ovládacích prvku.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aplikace ukládání do mezipaměti se rozumí předběžné načítání dat. K datům pak lze přistupovat bez další komunikace mezi procesy. Ukládání do mezipaměti se obvykle používá klientské aplikace Automatizace uživatelského rozhraní k načtení vlastností a vzory řízení hromadně. Informace jsou pak načteny z mezipaměti podle potřeby. Aplikace aktualizuje mezipaměť pravidelně, obvykle v reakci na události, které znamenají, že se něco v změnilo. [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]  
  
 Výhody ukládání do mezipaměti jsou nejvíce patrné s ovládacími prvky WPF (Windows Presentation Foundation) a vlastní mise, které mají zprostředkovatele automatizace uživatelského rozhraní na straně serveru. Při přístupu k zprostředkovatelům na straně klienta, jako jsou výchozí zprostředkovatelé pro ovládací prvky win32, je méně výhod.  
  
 Ukládání do mezipaměti dochází, když <xref:System.Windows.Automation.CacheRequest> aplikace aktivuje a pak používá <xref:System.Windows.Automation.AutomationElement>libovolnou metodu nebo vlastnost, která vrátí ; například <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. . Metody třídy <xref:System.Windows.Automation.TreeWalker> jsou výjimkou; ukládání do mezipaměti se <xref:System.Windows.Automation.CacheRequest> provádí pouze v případě, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>že je jako parametr zadán parametr (například .  
  
 Ukládání do mezipaměti také dochází, když <xref:System.Windows.Automation.CacheRequest> se přihlásíte k odběru události, zatímco je aktivní. Předáno <xref:System.Windows.Automation.AutomationElement> obslužné rutině události jako zdroj události obsahuje vlastnosti <xref:System.Windows.Automation.CacheRequest>a vzorky uložené v mezipaměti určené originálem . Všechny změny provedené <xref:System.Windows.Automation.CacheRequest> po přihlášení k odběru události nemají žádný vliv.  
  
 Vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a řídicí vzory prvku lze uložit do mezipaměti.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Možnosti pro ukládání do mezipaměti  
 Určuje <xref:System.Windows.Automation.CacheRequest> následující možnosti ukládání do mezipaměti.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Vlastnosti do mezipaměti  
 Vlastnosti pro ukládání do <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> mezipaměti můžete zadat voláním každé vlastnosti před aktivací požadavku.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Vzory ovládacích prvku do mezipaměti  
 Můžete určit vzorky ovládacího <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> prvku do mezipaměti voláním pro každý vzor před aktivací požadavku. Při ukládání vzoru do mezipaměti, jeho vlastnosti nejsou automaticky ukládány do mezipaměti; Je nutné zadat vlastnosti, které <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>chcete uložit do mezipaměti pomocí aplikace .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Rozsah a filtrování ukládání do mezipaměti  
 Můžete určit prvky, jejichž vlastnosti a vzorky, které chcete do mezipaměti nastavením <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> vlastnostpřed aktivací požadavku. Obor je relativní k prvky, které jsou načteny, zatímco požadavek je aktivní. Například pokud nastavíte pouze <xref:System.Windows.Automation.TreeScope.Children>a <xref:System.Windows.Automation.AutomationElement>potom načíst , vlastnosti a vzorky podřízené objekty tohoto prvku jsou uloženy do mezipaměti, ale ne ty prvku samotného. Chcete-li zajistit, že ukládání do mezipaměti se <xref:System.Windows.Automation.TreeScope.Element> provádí <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> pro načtený prvek sám, musíte zahrnout do vlastnosti. Není možné nastavit obor nebo <xref:System.Windows.Automation.TreeScope.Parent> <xref:System.Windows.Automation.TreeScope.Ancestors>. Nadřazený prvek však může být uložen do mezipaměti, když je podřízený prvek uložen do mezipaměti; Viz Načítání dětí a rodičů v mezipaměti v tomto tématu.  
  
 Rozsah ukládání do mezipaměti je <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> také ovlivněn vlastností. Ve výchozím nastavení se ukládání do mezipaměti provádí pouze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro prvky, které se zobrazí v ovládacím zobrazení stromu. Tuto vlastnost však můžete změnit tak, aby se ukládání do mezipaměti vztahovalo na všechny prvky nebo pouze na prvky, které se zobrazují v zobrazení obsahu.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Síla odkazů na elementy  
 Při načtení <xref:System.Windows.Automation.AutomationElement>, ve výchozím nastavení máte přístup ke všem vlastnostem a vzorky tohoto prvku, včetně těch, které nebyly uloženy do mezipaměti. Pro vyšší efektivitu však můžete určit, že odkaz na prvek odkazuje <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> pouze na <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None>data uložená v mezipaměti, nastavením vlastnosti do . V tomto případě nemáte přístup k žádné vlastnosti bez mezipaměti a vzory načtených prvků. To znamená, že nelze <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> získat `Current` přístup <xref:System.Windows.Automation.AutomationElement> k žádné vlastnosti prostřednictvím nebo vlastnost nebo jakýkoli vzor ovládacího prvku; ani nelze načíst vzor <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>pomocí nebo . Na vzorech uložených v mezipaměti můžete volat <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>metody, které načítají vlastnosti pole, <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>například , ale ne všechny, které provádějí akce s ovládacím prvkem, například .  
  
 Příkladem aplikace, která nemusí vyžadovat úplné odkazy na objekty, je program <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> pro čtení z obrazovky, který <xref:System.Windows.Automation.AutomationElement> by předem načítat vlastnosti a vlastnosti prvků v okně, ale nebude potřebovat samotné objekty.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Aktivace požadavku mezipaměti  
 Ukládání do mezipaměti <xref:System.Windows.Automation.AutomationElement> se provádí pouze <xref:System.Windows.Automation.CacheRequest> v případě, že jsou objekty načteny, když je aktivní pro aktuální vlákno. Existují dva způsoby <xref:System.Windows.Automation.CacheRequest>aktivace .  
  
 Obvyklým způsobem je <xref:System.Windows.Automation.CacheRequest.Activate%2A>volání . Tato metoda vrátí objekt, <xref:System.IDisposable>který implementuje . Požadavek zůstane aktivní tak <xref:System.IDisposable> dlouho, dokud objekt existuje. Nejjednodušší způsob, jak řídit životnost objektu je uzavřít volání `using` v rámci `Using` (C#) nebo (Visual Basic) bloku. Tím zajistíte, že požadavek bude odebrána ze zásobníku i v případě, že je vyvolána výjimka.  
  
 Dalším způsobem, který je užitečný, pokud chcete vnořit požadavky mezipaměti, je volání <xref:System.Windows.Automation.CacheRequest.Push%2A>. Tím umístí požadavek na zásobníku a aktivuje jej. Požadavek zůstane aktivní, dokud není <xref:System.Windows.Automation.CacheRequest.Pop%2A>odebrán ze zásobníku . Požadavek se dočasně stane neaktivní, pokud je do zásobníku posunut jiný požadavek. pouze nejvyšší požadavek v zásobníku je aktivní.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Načítání vlastností uložených v mezipaměti  
 Vlastnosti prvku uložené v mezipaměti můžete načíst pomocí následujících metod a vlastností.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Výjimka je vyvolána, pokud požadovaná vlastnost není v mezipaměti.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, <xref:System.Windows.Automation.AutomationElement.Current%2A>jako je , zpřístupňuje jednotlivé vlastnosti jako členy struktury. Však není nutné načíst tuto strukturu; můžete přistupovat k jednotlivým vlastnostem přímo. Vlastnost lze <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> například získat `element.Cached.Name`z `element` , <xref:System.Windows.Automation.AutomationElement>kde je .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Načítání vzorů řízení v mezipaměti  
 Vzory ovládacího prvku uložené v mezipaměti lze načíst pomocí následujících metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Pokud vzorek není v mezipaměti, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> vyvolá <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> výjimku a vrátí `false`.  
  
 Vlastnosti vzoru ovládacího prvku uložené v `Cached` mezipaměti můžete načíst pomocí vlastnosti objektu vzoru. Můžete také načíst aktuální `Current` hodnoty prostřednictvím <xref:System.Windows.Automation.AutomationElementMode.None> vlastnosti, ale <xref:System.Windows.Automation.AutomationElement> pouze v případě, že nebyl zadán při načtení. (<xref:System.Windows.Automation.AutomationElementMode.Full> je výchozí hodnota, která umožňuje přístup k aktuálním hodnotám.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Načítání dětí a rodičů v mezipaměti  
 Při načtení <xref:System.Windows.Automation.AutomationElement> a požádat o ukládání do <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> mezipaměti pro podřízené prvek prostřednictvím vlastnosti požadavku, je následně možné získat podřízené prvky z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> vlastnosti prvku, který jste načetli.  
  
 Pokud <xref:System.Windows.Automation.TreeScope.Element> byl zahrnut do oboru požadavku mezipaměti, kořenový prvek požadavku <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> je následně k dispozici z vlastnosti některého z podřízených prvků.  
  
> [!NOTE]
> Rodiče nebo předchůdci kořenového prvku požadavku nelze uložit do mezipaměti.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Aktualizace mezipaměti  
 Mezipaměť je platná pouze tehdy, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]pokud se v souboru . Aplikace je zodpovědná za aktualizaci mezipaměti, obvykle v reakci na události.  
  
 Pokud se přihlásíte k <xref:System.Windows.Automation.CacheRequest> odběru události, <xref:System.Windows.Automation.AutomationElement> když je aktivní, získáte s aktualizovanou mezipamětí jako zdrojem události při každém volání delegáta obslužné rutiny události. Informace uložené v mezipaměti prvku můžete <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>také aktualizovat voláním . Můžete předat v <xref:System.Windows.Automation.CacheRequest> originálu aktualizovat všechny informace, které byly dříve uloženy do mezipaměti.  
  
 Aktualizace mezipaměti nezmění vlastnosti existujících <xref:System.Windows.Automation.AutomationElement> odkazů.  
  
## <a name="see-also"></a>Viz také

- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Ukázka fetchtimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
