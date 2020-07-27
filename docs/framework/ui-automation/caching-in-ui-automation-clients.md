---
title: Práce s mezipamětí u klientů automatizace uživatelského rozhraní
description: Získejte podrobné informace o ukládání do mezipaměti v klientech automatizace uživatelského rozhraní v .NET. Ukládání do mezipaměti je definováno jako předběžná načítající data.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 4fbb4acabebea54015b11cefdf8a37c7e2dc93f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168254"
---
# <a name="caching-in-ui-automation-clients"></a>Práce s mezipamětí u klientů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma zavádí ukládání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností a vzorů ovládacích prvků do mezipaměti.  
  
 V systému [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je ukládání dat do mezipaměti znamená předem načítat data. Data je pak možné použít bez dalšího procesu komunikace mezi procesy. Mezipaměť obvykle používá klientské aplikace automatizace uživatelského rozhraní k hromadnému načítání vlastností a vzorů ovládacích prvků. Informace se pak z mezipaměti načítají podle potřeby. Aplikace pravidelně aktualizuje mezipaměť, obvykle v reakci na události značící, že došlo ke [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] změně.  
  
 Výhody ukládání do mezipaměti jsou s největší výpovědí s ovládacími prvky Windows Presentation Foundation (WPF) a vlastními ovládacími prvky, které mají zprostředkovatele automatizace uživatelského rozhraní na straně serveru. Při přístupu k poskytovatelům na straně klienta, jako jsou výchozí zprostředkovatelé pro řízení systému Win32, je méně výhodná.  
  
 K ukládání do mezipaměti dojde, když aplikace aktivuje <xref:System.Windows.Automation.CacheRequest> a pak používá jakoukoli metodu nebo vlastnost, která vrací, <xref:System.Windows.Automation.AutomationElement> například <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> , <xref:System.Windows.Automation.AutomationElement.FindAll%2A> . Metody <xref:System.Windows.Automation.TreeWalker> třídy jsou výjimkou. ukládání do mezipaměti je provedeno pouze v případě <xref:System.Windows.Automation.CacheRequest> , že je zadán jako parametr (například <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType> .  
  
 K ukládání do mezipaměti dojde také v případě, že se přihlásíte k odběru události, když <xref:System.Windows.Automation.CacheRequest> je aktivní. <xref:System.Windows.Automation.AutomationElement>Předané obslužné rutině události jako zdroj události obsahuje vlastnosti a vzory v mezipaměti, které jsou určeny původní <xref:System.Windows.Automation.CacheRequest> . Jakékoli změny provedené v <xref:System.Windows.Automation.CacheRequest> po přihlášení k odběru události nebudou nijak ovlivněny.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnosti a vzory ovládacích prvků prvku mohou být uloženy do mezipaměti.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Možnosti ukládání do mezipaměti  
 <xref:System.Windows.Automation.CacheRequest>Určuje následující možnosti pro ukládání do mezipaměti.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Vlastnosti do mezipaměti  
 Můžete zadat vlastnosti pro ukládání do mezipaměti voláním <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> pro každou vlastnost před aktivací žádosti.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Vzory ovládacích prvků pro ukládání do mezipaměti  
 Můžete zadat vzory řízení pro ukládání do mezipaměti voláním <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> pro každý vzor před aktivací žádosti. Když je vzor uložen do mezipaměti, jeho vlastnosti nejsou automaticky uloženy v mezipaměti. je nutné zadat vlastnosti, které chcete uložit do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType> .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Rozsah a filtrování ukládání do mezipaměti  
 Můžete určit prvky, jejichž vlastnosti a vzory chcete ukládat do mezipaměti, nastavením <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> vlastnosti před aktivací žádosti. Obor je relativní vzhledem k prvkům, které jsou načteny v době, kdy je požadavek aktivní. Například pokud nastavíte pouze <xref:System.Windows.Automation.TreeScope.Children> a poté načtete <xref:System.Windows.Automation.AutomationElement> , vlastnosti a vzory podřízených prvků tohoto prvku jsou uloženy v mezipaměti, ale nikoli samotného elementu. Aby bylo zajištěno, že ukládání do mezipaměti je provedeno pro samotný načtený prvek, musíte zahrnout <xref:System.Windows.Automation.TreeScope.Element> do <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> Vlastnosti. Není možné nastavit obor na <xref:System.Windows.Automation.TreeScope.Parent> nebo <xref:System.Windows.Automation.TreeScope.Ancestors> . Nadřazený element však může být uložen do mezipaměti, pokud je podřízený element uložen v mezipaměti; viz načtení podřízených objektů a rodičů v mezipaměti v tomto tématu.  
  
 Velikost ukládání do mezipaměti je ovlivněna také <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> vlastností. Ve výchozím nastavení se ukládání do mezipaměti provádí pouze pro prvky, které se zobrazí v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury. Tuto vlastnost však můžete změnit na možnost použít ukládání do mezipaměti pro všechny prvky nebo pouze na prvky, které se zobrazí v zobrazení obsahu.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Síla odkazů na prvky  
 Když načtete <xref:System.Windows.Automation.AutomationElement> , ve výchozím nastavení máte přístup ke všem vlastnostem a vzorům daného prvku, včetně těch, které nebyly uloženy v mezipaměti. Pro vyšší efektivitu však můžete určit, že odkaz na prvek odkazuje pouze na data uložená v mezipaměti nastavením <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnosti na <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None> . V takovém případě nebudete mít přístup k žádným vlastnostem a vzorům načtených prvků, které nejsou uložené v mezipaměti. To znamená, že nemůžete získat přístup k žádným vlastnostem prostřednictvím <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo pomocí `Current` vlastnosti <xref:System.Windows.Automation.AutomationElement> nebo žádného vzoru ovládacího prvku; ani nelze načíst vzor pomocí <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> . U vzorů v mezipaměti můžete volat metody, které načítají vlastnosti pole, například <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType> , ale ne všechny, které provádějí akce na ovládacím prvku, například <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType> .  
  
 Příkladem aplikace, která nemusí potřebovat úplné odkazy na objekty, je čtečka obrazovky, která by vyvolala <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastnosti a prvků v okně, ale nemusela <xref:System.Windows.Automation.AutomationElement> objekty samotné.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Aktivace třídu CacheRequest  
 Ukládání do mezipaměti je provedeno pouze v případě, že <xref:System.Windows.Automation.AutomationElement> jsou objekty načteny v době, kdy <xref:System.Windows.Automation.CacheRequest> je aktivní pro aktuální vlákno. Existují dva způsoby, jak aktivovat <xref:System.Windows.Automation.CacheRequest> .  
  
 Obvyklým způsobem je zavolat <xref:System.Windows.Automation.CacheRequest.Activate%2A> . Tato metoda vrací objekt, který implementuje <xref:System.IDisposable> . Požadavek zůstane aktivní, dokud <xref:System.IDisposable> objekt existuje. Nejjednodušší způsob, jak řídit životnost objektu, je uzavřít volání do `using` bloku (C#) nebo `Using` (Visual Basic). Tím se zajistí, že se požadavek z zásobníku odebere i v případě, že se vyvolá výjimka.  
  
 Dalším způsobem, který je užitečný, když chcete vnořit požadavky do mezipaměti, je zavolat <xref:System.Windows.Automation.CacheRequest.Push%2A> . Tím se požadavek vloží do zásobníku a aktivuje se. Požadavek zůstane aktivní, dokud jej z zásobníku neodeberete <xref:System.Windows.Automation.CacheRequest.Pop%2A> . Požadavek se bude dočasně neaktivní, pokud se do zásobníku vloží další požadavek. aktivní je jenom nejvyšší požadavek v zásobníku.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Načítání vlastností uložených v mezipaměti  
 Pomocí následujících metod a vlastností lze načíst vlastnosti prvku uložené v mezipaměti.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Pokud požadovaná vlastnost není v mezipaměti, je vyvolána výjimka.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, podobně jako <xref:System.Windows.Automation.AutomationElement.Current%2A> , zpřístupňuje jednotlivé vlastnosti jako členy struktury. Tuto strukturu ale nemusíte načítat. k jednotlivým vlastnostem můžete přistupovat přímo. <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>Vlastnost lze například získat z `element.Cached.Name` , kde `element` je <xref:System.Windows.Automation.AutomationElement> .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Načítání vzorů ovládacích prvků v mezipaměti  
 Můžete načíst vzory ovládacích prvků v mezipaměti prvku prostřednictvím následujících metod.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Pokud vzorek není v mezipaměti, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> vyvolá výjimku a <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> vrátí `false` .  
  
 Vlastnosti v mezipaměti vzoru ovládacího prvku lze načíst pomocí `Cached` vlastnosti objektu vzoru. Aktuální hodnoty lze také načíst prostřednictvím `Current` vlastnosti, ale pouze v případě, že <xref:System.Windows.Automation.AutomationElementMode.None> při načtení byla zadána <xref:System.Windows.Automation.AutomationElement> . ( <xref:System.Windows.Automation.AutomationElementMode.Full> je výchozí hodnota, která umožňuje přístup k aktuálním hodnotám.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Načítání podřízených a podřízených objektů v mezipaměti  
 Když načtete <xref:System.Windows.Automation.AutomationElement> a vyžádáte ukládání do mezipaměti pro podřízené položky daného elementu prostřednictvím <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnosti žádosti, je možné získat podřízené prvky z <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> vlastnosti elementu, který jste načetli.  
  
 Pokud <xref:System.Windows.Automation.TreeScope.Element> byl zahrnut do oboru žádosti o mezipaměť, kořenový prvek požadavku je následně dostupný z <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> vlastnosti všech podřízených elementů.  
  
> [!NOTE]
> Nemůžete ukládat do mezipaměti nadřazené prvky nebo předchůdce kořenového elementu požadavku.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Aktualizace mezipaměti  
 Mezipaměť je platná pouze tak dlouho, dokud se nemění žádné změny v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Vaše aplikace zodpovídá za aktualizaci mezipaměti, obvykle v reakci na události.  
  
 Pokud se přihlásíte k odběru události <xref:System.Windows.Automation.CacheRequest> , když je aktivní, získáte <xref:System.Windows.Automation.AutomationElement> s aktualizovanou mezipamětí jako zdroj události vždy, když je volána obslužná rutina obslužné rutiny události. Můžete také aktualizovat informace uložené v mezipaměti pro element voláním <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A> . <xref:System.Windows.Automation.CacheRequest>K aktualizaci všech informací, které byly dříve uloženy v mezipaměti, můžete předat originál.  
  
 Aktualizace mezipaměti nemění vlastnosti jakýchkoli existujících <xref:System.Windows.Automation.AutomationElement> odkazů.  
  
## <a name="see-also"></a>Viz také

- [Události automatizace uživatelského rozhraní pro klienty](ui-automation-events-for-clients.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Ukázka FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
