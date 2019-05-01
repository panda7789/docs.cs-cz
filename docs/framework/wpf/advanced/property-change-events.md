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
ms.openlocfilehash: b6f625f76e230b7d6bf0488bfa75c227de31a5d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62030300"
---
# <a name="property-change-events"></a>Události změny vlastnosti
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] definuje několik událostí, které jsou vyvolány v reakci na změnu v hodnotě vlastnosti. Vlastnost je často vlastnost závislosti. Samotné události je někdy směrované události a v některých případech je standard [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] událostí. Definice události se liší v závislosti na scénáři, protože některé změny vlastností se více odpovídajícím způsobem směrovaná přes stromu, zatímco jiné změny vlastností jsou obecně jen zájmu změnou vlastnosti objektu.  
  
## <a name="identifying-a-property-change-event"></a>Určení události změny vlastnosti  
 Ne všechny události, které se nahlásit změnu vlastnosti jsou explicitně označeny jako událost změněné vlastnosti, buď tím, že vzor podpis nebo vzor pojmenování. Obecně platí, popis události v [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentaci Určuje, jestli událostí přímo souvisí ke změně hodnoty vlastnosti a obsahuje křížové odkazy mezi vlastností a událostí.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged Events  
 Určité události použít datový typ události a delegát, který se explicitně používají pro události změny vlastnosti. Datový typ události je <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, a je delegát <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Data události a delegátem mít parametr obecného typu, který je možné určit skutečný typ změny vlastnosti při definování obslužné rutiny. Data událostí obsahují dvě vlastnosti <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, které jsou pak předán jako argument typu události data.  
  
 "Trasované" část názvu označuje, že událost změněné vlastnosti je registrován jako směrované události. Výhodou směrování událost změněné vlastnosti je, že nejvyšší úrovni ovládací prvek může přijímat události změněné vlastnosti, pokud hodnoty změnit vlastnosti na podřízené prvky (složeného ovládacího prvku části). Například můžete vytvořit ovládací prvek, který zahrnuje <xref:System.Windows.Controls.Primitives.RangeBase> ovládací prvek, jako <xref:System.Windows.Controls.Slider>. Pokud hodnota <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> změny vlastností v části posuvník, můžete chtít zpracovat tuto změnu na nadřazený ovládací prvek a nikoli na části.  
  
 Protože máte staré hodnoty a novou hodnotu, může být lákavé použít tuto obslužnou rutinu události jako validátor pro hodnotu vlastnosti. Ale to není návrhu záměr většina události změněné vlastnosti. Obecně platí hodnoty jsou k dispozici, aby mohli pracovat s těmito hodnotami v jiných oblastech logiku kódu, ale ve skutečnosti změna hodnot z v rámci obslužné rutiny události není vhodné a může způsobit nechtěné rekurzi v závislosti na tom, jak je implementované vaše obslužná rutina .  
  
 Pokud vaše je vlastní závislost vlastnost, nebo pokud pracujete s odvozené třídy kde jste definovali kódu instance, je mnohem lepší mechanismus pro sledování změn vlastnosti, které je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému vlastností: zpětná volání systému vlastnost <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>. Další informace o tom, jak můžete používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systém pro ověřování polí a vynucení, přečtěte si [vlastnost závislosti zpětné volání a ověření](dependency-property-callbacks-and-validation.md) a [vlastní vlastnosti závislosti](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged události  
 Je jinou dvojici typů, které jsou součástí scénáře událost změněné vlastnosti <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler>. Události změny vlastnosti nejsou směrovány; jsou standardní [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] události. <xref:System.Windows.DependencyPropertyChangedEventArgs> je neobvyklé události datový typ vytváření sestav, protože není odvozena od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> je struktura, není třída.  
  
 Události, které používají <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler> jsou mírně častější než `RoutedPropertyChanged` události. Je například událost, která používá tyto typy <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Stejně jako <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> taky sestavy o staré a nové hodnotu pro vlastnost. Také stejné důležité informace o tom, co vám může s hodnotami použít; Obecně není doporučeno, pokusíte-li ke změně hodnot znovu na odesílatele v reakci na události.  
  
## <a name="property-triggers"></a>Aktivační procedury vlastností  
 Úzce související konceptem pro událost změněné vlastnosti jsou aktivační procedura vlastností. Aktivační procedura vlastností v rámci stylu nebo šablony a umožňuje vytvářet podmíněné chování na základě hodnoty vlastnosti, kde je přiřazený aktivační procedura vlastností.  
  
 Vlastnosti aktivační události vlastnost musí být vlastnost závislosti. To může být (a často je) vlastnosti závislosti jen pro čtení. Jasně ukazuje pro při se aspoň částečně navržena jako aktivační procedura vlastností vlastnost závislosti vystavené ovládací prvek je, pokud název začíná řetězcem "Je". Vlastnosti, které mají tato pojmenování jsou často vlastnosti závislosti jen pro čtení logická kde primární scénáře pro vlastnost hlásí stav ovládacího prvku, který může mít následky na uživatelské rozhraní v reálném čase a je proto Release candidate aktivační události vlastnost.  
  
 Některé z těchto vlastností je navíc událost změněné vlastnosti vyhrazené. Například vlastnost <xref:System.Windows.UIElement.IsMouseCaptured%2A> má událost změněné vlastnosti <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Samotná hodnota vlastnosti je jen pro čtení, s upravit tak, že vstupní systém hodnotou a vstupní systém vyvolá <xref:System.Windows.UIElement.IsMouseCapturedChanged> při každé změně v reálném čase.  
  
 Ve srovnání s událost změněné vlastnosti na hodnotu true, použití aktivační procedura vlastností tak, aby fungoval na změnu vlastnosti má určitá omezení.  
  
 Seznámení se základními přesnou shodu logiku aktivační procedury vlastností. Zadejte vlastnosti a hodnotu, která označuje určitou hodnotu, pro kterou bude trigger fungovat. Například: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Vzhledem k tomuto omezení bude většinu vlastností aktivační událost použití logické vlastnosti nebo vlastnosti, které nabývat hodnoty vyhrazených výčet, kde je dostatečně spravovatelné k definování aktivační událost pro každý případ rozsah možných hodnot. Aktivační procedury vlastností může existovat pouze pro zvláštní hodnoty, například když počet položek dosáhne nuly, nebo by existovat žádná aktivační událost, která při změně hodnoty vlastnosti směrem od nuly znovu pro účty pro případy (místo aktivační události pro všechny případy, musíte kód Obslužná rutina události tady, nebo výchozí chování, která se přepne zpět z aktivační události stavu znovu, pokud je hodnota nenulová).  
  
 Syntaxe vlastnosti aktivační události je obdobná příkaz "if" v programování. Pokud je aktivační podmínka pravdivá, pak "tělem" aktivační procedura vlastností je "spustit". "Tělem" aktivační procedura vlastností není kód, je kód. Tento kód je omezen na použití jednoho nebo více <xref:System.Windows.Setter> prvků, které mají nastavit další vlastnosti objektu, kde se právě používá styl nebo šablonu.  
  
 Odsazení podmínky "if" aktivační události vlastnost, která má širokou škálu možných hodnot, je obecně vhodné nastavit stejnou hodnotu vlastnosti na výchozí hodnotu pomocí <xref:System.Windows.Setter>. Tímto způsobem <xref:System.Windows.Trigger> omezením setter bude mít přednost, pokud nastane aktivační podmínka a <xref:System.Windows.Setter> , který není v rozsahu <xref:System.Windows.Trigger> bude mít přednost pokaždé, když se trigger podmínka není splněna.  
  
 Aktivační procedury vlastností jsou obecně vhodné pro scénáře, ve kterém by měl změnit jednu nebo více vlastností vzhled, na základě stavu jinou vlastnost u stejného elementu.  
  
 Další informace o aktivační procedury vlastností najdete v tématu [styly a šablony](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
