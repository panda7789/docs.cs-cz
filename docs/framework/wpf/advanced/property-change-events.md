---
title: Události změny vlastnosti
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: ac2a44eb92e384851bbe6ac860fd9b46d3377a06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="property-change-events"></a>Události změny vlastnosti
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] definuje několik událostí, které jsou vyvolány v reakci na změnu v hodnotě vlastnosti. Vlastnost často je vlastnost závislosti. Samotné události je někdy směrované události a v některých případech je standard [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] událostí. Definice události se liší v závislosti na scénáři, protože některé vlastnosti změny více správně směrování v stromu k elementu, zatímco jiné změny vlastnosti jsou obecně pouze o problém k objektu, kde vlastnost změnit.  
  
## <a name="identifying-a-property-change-event"></a>Identifikace událost změny vlastnosti  
 Ne všechny události, které nahlásit změnu vlastnosti jsou explicitně označeny jako událost změněné vlastnosti, buď na základě vzoru podpis nebo vzoru pro pojmenovávání. Obecně platí, popis události v [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentace Určuje, jestli události je přímo vázaný na změně hodnoty vlastnosti a poskytuje křížové odkazy mezi vlastností a událostí.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged události  
 Určité události použijte datový typ události a delegáta, který se explicitně používají pro události změny vlastnosti. Datový typ události je <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, a je delegát <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Data události a delegáta mít parametr obecného typu, který slouží k určení skutečný typ změny vlastnosti, když definujete, aby obslužná rutina. Data události obsahuje dvě vlastnosti <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, které jsou obě předána jako argument typu události data.  
  
 "Směrován" část názvu označuje, že událost změněné vlastnosti je registrován jako směrované události. Výhodou událost změněné vlastnosti směrování je, že nejvyšší úrovně ovládacího prvku může přijímat události změněné vlastnosti, pokud hodnoty změnit vlastnosti podřízené elementy (složeného ovládacího prvku části). Můžete například vytvořit ovládací prvek, který zahrnuje <xref:System.Windows.Controls.Primitives.RangeBase> například řízení <xref:System.Windows.Controls.Slider>. Pokud hodnota <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> změny vlastností v rámci posuvník, můžete se zpracovat tuto změnu na nadřazeného ovládacího prvku ne na části.  
  
 Vzhledem k tomu, že máte stará hodnota a nová hodnota, může to být tempting má používat jako validátor této obslužné rutiny události pro hodnotu vlastnosti. Ale, který není záměrem návrhu většina události změněné vlastnosti. Obecně platí jsou k dispozici, aby s těmito hodnotami v jiných oblastech logiku kódu mohli pracovat, ale ve skutečnosti změna hodnoty z v rámci obslužné rutiny události není vhodné hodnoty a může způsobit nechtěné rekurze v závislosti na tom, jak je implementována vaší obslužné rutiny .  
  
 Pokud vaše je vlastnost vlastní závislosti, nebo pokud pracujete s odvozené třídě kde jste definovali kód vytváření instancí, je mnohem lepší mechanismus pro sledování změn vlastnosti, které je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému: zpětná volání vlastnost systému <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>. Další podrobnosti o tom, jak můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systém pro ověřování a převod, viz [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) a [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged události  
 Je jinou dvojici typů, které jsou součástí scénáři událost změněné vlastnosti <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler>. Události pro změny tyto vlastnosti nejsou směrovány; jsou standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. <xref:System.Windows.DependencyPropertyChangedEventArgs> je data neobvyklé události vytváření sestav typu, protože není odvozena od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> je struktura, ne třídu.  
  
 Události, které používají <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler> jsou mírně častější než `RoutedPropertyChanged` události. Je například událost, která používá tyto typy <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Jako <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> také sestavy starý a nový hodnotu pro vlastnost. Také stejné aspekty o si můžete pomocí hodnoty použít; se obecně nedoporučuje, pokusíte-li ke změně hodnot znovu na odesílatel v reakci na událost.  
  
## <a name="property-triggers"></a>Vlastnost aktivační události  
 Úzce související koncept jako událost změněné vlastnosti je vlastnost aktivační událost. Vlastnost aktivační událost se vytvoří v rámci styl nebo šablony a umožňuje vytvářet podmíněného chování na základě hodnoty vlastností, kde je přiřazena vlastnost aktivační události.  
  
 Vlastnost pro vlastnost aktivační událost musí být vlastnost závislosti. Ho může být (a často) vlastnost závislosti jen pro čtení. Dobrým ukazatelem pro když je vlastnost závislosti vystavené ovládacího prvku aspoň částečně navržený jako vlastnost aktivační událost je, pokud název vlastnosti začíná "Je". Vlastnosti, které mají tato pojmenování jsou často vlastnost jen pro čtení Boolean závislosti kde je primární scénář pro vlastnost generování sestav řízení stavu, který může mít důsledky pro rozhraní v reálném čase a je proto kandidátem vlastnost aktivační události.  
  
 Některé z těchto vlastností mít také událost změněné vlastnosti vyhrazené. Například vlastnost <xref:System.Windows.UIElement.IsMouseCaptured%2A> má událost změněné vlastnosti <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Samotné vlastnosti je jen pro čtení s hodnotou vstupní systémem upraví a vyvolá vstupní systému <xref:System.Windows.UIElement.IsMouseCapturedChanged> při každé změně v reálném čase.  
  
 Ve srovnání s událost změněné vlastnosti na hodnotu true, pomocí vlastnosti aktivační události tak, aby fungoval na změnu vlastnosti má určitá omezení.  
  
 Vlastnost aktivační události fungovat prostřednictvím logiku přesnou shodu. Určete vlastnosti a hodnotu, která určuje konkrétní hodnotu, pro který bude fungovat aktivační událost. Například: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Vzhledem k tomuto omezení budou většina vlastnost aktivační událost použití logická hodnota vlastnosti a vlastnosti, které trvat hodnota vyhrazené výčtu, kde je dostatečně spravovat k definování aktivační událost pro každý případ rozsah možných hodnot. Vlastnost aktivační události může existovat jenom pro speciální hodnoty, například když počet položek hodnota nula, a by existovat žádné aktivační událost, která účty v případech, při změně hodnoty vlastnosti směrem od nuly znovu (místo aktivačních událostí pro všechny případy, může být nutné kód obslužné rutiny události tady, nebo výchozí chování, která přepíná zpět z aktivace stavu znovu, pokud je hodnota nenulové hodnoty).  
  
 Syntaxe vlastnost aktivační události je obdobou příkazu "Pokud" při programování. Pokud je splněna podmínka aktivace, pak "text" vlastnost aktivační událost se spustí. "Text" vlastnost aktivační událost není kód, je značek. Tento kód je omezena na použití jednoho nebo více <xref:System.Windows.Setter> elementy nastavit další vlastnosti v objektu, kde se aplikuje styl nebo šablony.  
  
 K posunutí podmínku "Pokud" vlastnost aktivační událost, která má celou řadu možných hodnot, je většinou vhodné nastavit pomocí stejné hodnoty vlastnosti na výchozí <xref:System.Windows.Setter>. Tímto způsobem <xref:System.Windows.Trigger> obsažené setter bude mít přednost, pokud je nastavena hodnota true, podmínky spuštění a <xref:System.Windows.Setter> , není v rozsahu <xref:System.Windows.Trigger> bude mít přednost vždy, když je aktivační podmínka vyhodnocena jako false.  
  
 Vlastnost aktivační události jsou obecně vhodné pro scénáře, kde by se měl změnit jednu nebo více vlastností vzhled, na základě stavu jinou vlastnost u stejného elementu.  
  
 Další informace o aktivační události vlastnost najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
