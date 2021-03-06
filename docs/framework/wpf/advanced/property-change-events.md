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
ms.openlocfilehash: 68be4c6bf7cce8a3aeb928e1f0b0e8131263320c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459339"
---
# <a name="property-change-events"></a>Události změny vlastnosti
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] definuje několik událostí, které jsou vyvolány v reakci na změnu hodnoty vlastnosti. Vlastnost je často vlastnost závislosti. Samotná událost je někdy směrována jako událost, která je někdy standardní událostí modulu CLR (Common Language Runtime). Definice události se liší v závislosti na scénáři, protože některé změny vlastností jsou vhodně směrovány prostřednictvím stromu elementu, zatímco jiné změny vlastností jsou obecně pouze obavy o objekt, u kterého byla vlastnost změněna.  
  
## <a name="identifying-a-property-change-event"></a>Identifikace události změny vlastnosti  
 Ne všechny události, které nastavují změnu vlastnosti, se explicitně identifikují jako událost změněné vlastností, a to buď na základě vzoru podpisu, nebo podle vzoru pojmenování. Obecně popis události v dokumentaci k sadě SDK označuje, zda je událost přímo vázaná na změnu hodnoty vlastnosti a poskytuje křížové odkazy mezi vlastností a událostí.  
  
### <a name="routedpropertychanged-events"></a>Události RoutedPropertyChanged  
 Určité události používají datový typ události a delegáty, které jsou explicitně používány pro události změny vlastností. Datový typ události je <xref:System.Windows.RoutedPropertyChangedEventArgs%601>a delegát je <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Data události a Delegáti mají parametr obecného typu, který se používá k určení skutečného typu vlastnosti změny při definování obslužné rutiny. Data události obsahují dvě vlastnosti <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, které jsou následně předány jako argument typu v datech události.  
  
 Část "směrované" název označuje, že událost změny vlastnosti je registrována jako směrovaná událost. Výhodou směrování události změněné vlastnosti je, že nejvyšší úroveň ovládacího prvku může přijímat události změněné vlastností, pokud vlastnosti podřízených prvků (složené části ovládacího prvku) mění hodnoty. Například můžete vytvořit ovládací prvek, který zahrnuje <xref:System.Windows.Controls.Primitives.RangeBase> ovládací prvek, jako je například <xref:System.Windows.Controls.Slider>. Pokud se hodnota vlastnosti <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> mění v části posuvníku, může být vhodné tuto změnu zpracovat v nadřazeném ovládacím prvku, nikoli na části.  
  
 Vzhledem k tomu, že máte starou hodnotu a novou hodnotu, může se tato obslužná rutina události zvážit jako validátor pro hodnotu vlastnosti. Nejedná se ale o záměr návrhu většiny událostí změněných vlastností. Obecně jsou tyto hodnoty k dispozici, takže můžete pracovat s těmito hodnotami v jiných logických oblastech vašeho kódu, ale ve skutečnosti se změna hodnot z obslužné rutiny události nedá doporučit a může dojít k neúmyslnému rekurzi v závislosti na tom, jak je obslužná rutina implementovaná. .  
  
 Pokud je vaše vlastnost vlastní vlastností závislosti nebo pokud pracujete s odvozenou třídou, kde jste definovali kód vytváření instancí, existuje mnohem lepší mechanismus pro sledování změn vlastností, které jsou integrované v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m systému vlastností: vlastnost zpětná volání systému <xref:System.Windows.CoerceValueCallback> a <xref:System.Windows.PropertyChangedCallback>. Další podrobnosti o tom, jak můžete použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému vlastností pro ověřování a vynucení, najdete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md) a [vlastní vlastnosti závislosti](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Události DependencyPropertyChanged  
 Další dvojicí typů, které jsou součástí scénáře události změněné vlastnosti, je <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler>. Události pro tyto změny vlastností nejsou směrovány; jsou to standardní události CLR. <xref:System.Windows.DependencyPropertyChangedEventArgs> je neobvyklý typ generování sestav dat událostí, protože není odvozen od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> je struktura, nikoli třída.  
  
 Události, které používají <xref:System.Windows.DependencyPropertyChangedEventArgs> a <xref:System.Windows.DependencyPropertyChangedEventHandler> jsou poněkud běžnější než události `RoutedPropertyChanged`. Příklad události, která používá tyto typy, je <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Stejně jako <xref:System.Windows.RoutedPropertyChangedEventArgs%601><xref:System.Windows.DependencyPropertyChangedEventArgs> také hlásí starou a novou hodnotu pro vlastnost. Také platí stejné informace o tom, co můžete s hodnotami provádět; Obecně se nedoporučuje, abyste znovu změnili hodnoty u odesilatele v reakci na událost.  
  
## <a name="property-triggers"></a>Triggery vlastností  
 Úzce související koncept k události změněné vlastnosti je aktivační událost vlastnosti. Aktivační událost vlastnosti je vytvořena v rámci stylu nebo šablony a umožňuje vytvořit podmíněné chování na základě hodnoty vlastnosti, kde je přiřazena aktivační událost vlastnosti.  
  
 Vlastnost triggeru vlastnosti musí být vlastnost závislosti. Může to být (a často je) vlastnost závislosti jen pro čtení. Dobrý indikátor pro případ, že vlastnost závislosti vystavená ovládacím prvkem je alespoň částečně navržená tak, aby byla triggerem vlastnosti, je, že název vlastnosti začíná na "is". Vlastnosti, které mají tento názvový server, jsou často vlastností závislosti, která je jen pro čtení, přičemž primární scénář pro vlastnost je stav ovládacího prvku pro vytváření sestav, který může mít vliv na uživatelské rozhraní v reálném čase a je tedy kandidátem na triggery vlastností.  
  
 Některé z těchto vlastností mají také událost změny vyhrazené vlastnosti. Vlastnost <xref:System.Windows.UIElement.IsMouseCaptured%2A> má například <xref:System.Windows.UIElement.IsMouseCapturedChanged>události změněné vlastností. Samotná vlastnost je jen pro čtení a její hodnota je upravena vstupním systémem a vstupní systém vyvolá <xref:System.Windows.UIElement.IsMouseCapturedChanged> při každé změně v reálném čase.  
  
 V porovnání s událostí změněné vlastnosti true má použití triggeru vlastnosti k tomu, aby fungovalo u změny vlastnosti.  
  
 Triggery vlastností fungují přes přesnou logiku shody. Zadáte vlastnost a hodnotu, která určuje konkrétní hodnotu, pro kterou bude aktivační událost fungovat. Příklad: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Z důvodu tohoto omezení je většina použití triggeru vlastností pro logické vlastnosti nebo vlastnosti, které přijímají hodnotu vyhrazeného výčtu, kde je možné rozsah hodnot dostatečně spravovat, aby bylo možné definovat Trigger pro každý případ. Triggery vlastností nebo se můžou vyskytovat jenom pro speciální hodnoty, třeba když počet položek dosáhne nuly, a nespustí se žádná aktivační událost, která by pro případy, kdy se hodnota vlastnosti změní směrem od nuly (místo triggerů pro všechny případy), nemusela být potřebná. sem patří obslužná rutina události nebo výchozí chování, které přepne zpátky ze stavu triggeru znovu, pokud je hodnota nenulová.  
  
 Syntaxe triggeru vlastnosti je analogická k příkazu "If" v programování. Pokud má podmínka triggeru hodnotu true, pak je "tělo" triggeru vlastnosti "spuštěno". "Tělo" triggeru vlastnosti není kód, je značkami. Tento kód je omezen na použití jednoho nebo více <xref:System.Windows.Setter> prvků pro nastavení dalších vlastností objektu, ve kterém je použit styl nebo šablona.  
  
 Pro posunutí podmínky "Pokud" triggeru vlastnosti, který má širokou škálu možných hodnot, je obecně vhodné nastavit stejnou hodnotu vlastnosti na výchozí pomocí <xref:System.Windows.Setter>. To znamená, že <xref:System.Windows.Trigger> s tímto nastavením bude mít přednost, pokud je podmínka triggeru pravdivá a <xref:System.Windows.Setter>, která není v rámci <xref:System.Windows.Trigger>, bude mít přednost, kdykoliv je podmínka triggeru nepravdivá.  
  
 Triggery vlastností jsou obecně vhodné pro scénáře, ve kterých se má změnit jedna nebo více vlastností vzhledu na základě stavu jiné vlastnosti stejného prvku.  
  
 Další informace o aktivačních událostech vlastností naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
