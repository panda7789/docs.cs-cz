---
title: Zpracování událostí v jazyku Visual Basic a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 321b4547bffbbae3c16ef8dd046bdff65ebe0bf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547820"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Zpracování událostí v jazyku Visual Basic a WPF
Pro jazyk Visual Basic .NET Microsoft konkrétně, můžete použít konkrétní jazyk `Handles` – klíčové slovo přidružit obslužné rutiny událostí s instancemi místo připojení obslužných rutin událostí pomocí atributů nebo pomocí <xref:System.Windows.UIElement.AddHandler%2A> metoda. Ale `Handles` technika pro připojení k instancím obslužných rutin mají určitá omezení, protože `Handles` syntaxe nepodporuje některé funkce konkrétní směrované události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému.  
  
## <a name="using-handles-in-a-wpf-application"></a>Použití "Popisovače" v aplikaci WPF  
 Obslužné rutiny událostí, které jsou připojené k instancí a událostí pomocí `Handles` musí všechny být definován v rámci třídu deklaraci instance, která je také požadavek pro obslužné rutiny událostí, které jsou přiřazeny pomocí hodnoty atributu na elementy. Můžete zadat jenom `Handles` pro element na stránce, který má <xref:System.Windows.FrameworkContentElement.Name%2A> hodnota vlastnosti (nebo [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md) deklarovaný). Důvodem je, že <xref:System.Windows.FrameworkContentElement.Name%2A> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vytvoří odkaz na instance, které jsou nezbytné pro podporu *Instance.Event* vyžadovanou formát reference `Handles` syntaxe. Jediným prvkem, který lze použít pro `Handles` bez <xref:System.Windows.FrameworkContentElement.Name%2A> odkaz je kořenový element instanci, která definuje třídu.  
  
 Obslužná rutina stejné můžete přiřadit víc elementů oddělením *Instance.Event* odkazuje po `Handles` čárkami.  
  
 Můžete použít `Handles` přiřadit více než jeden obslužné rutiny na stejnou *Instance.Event*odkaz. Nepřiřazujte žádné důležitosti pořadí, ve kterém jsou uvedeny obslužné rutiny v `Handles` odkazovat; musí předpokládat, že obslužné rutiny, které zpracovávají stejnou událost nelze vyvolat v libovolném pořadí.  
  
 Chcete-li odebrat obslužnou rutinu, která byla přidána se `Handles` v deklaraci, můžete volat <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Můžete použít `Handles` připojit obslužné rutiny pro směrované události, tak dlouho, dokud připojení obslužné rutiny instancí, které definování události ke zpracování v jejich členové tabulky. Pro směrované události, obslužné rutiny, které jsou připojené k `Handles` postupujte podle stejné pravidla směrování, stejně jako obslužné rutiny, které jsou připojené jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributů, nebo pomocí běžných podpis <xref:System.Windows.UIElement.AddHandler%2A>. To znamená, že pokud události je již označena jako zpracovaná ( <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost v datech události je `True`), pak obslužné rutiny připojené k `Handles` nejsou v odpovědi na tuto instanci událost vyvolána. Událost může být označen zpracovávaný instance obslužné rutiny na jiný element ve trasy, nebo podle třídy zpracování buď na aktuálního elementu nebo dřívějších elementů na trase. Pro vstupní události, které podporují události spárované tunelové propojení nebo bublin mohou tunelového propojení směrování označeny pár událostí zpracovává. Další informace o směrované události najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Omezení "Popisovače" pro přidání obslužné rutiny  
 `Handles` nemůže odkazovat na obslužné rutiny pro přidružené události. Je nutné použít `add` metoda přistupujícího objektu pro tuto událost připojené nebo *typename.eventname* událostí atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podrobnosti najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Pro směrované události lze použít pouze `Handles` přiřadit obslužné rutiny pro instance, kde tuto událost existuje v tabulce členů instance. Však s směrované události obecně nadřazený element může být naslouchací proces pro událost z podřízených elementů i v případě, že nadřazený element nemá tuto událost v tabulce její členy. V atributu syntaxe, můžete zadat to prostřednictvím *typename.membername* atribut formulář, který kvalifikuje typů, které se ve skutečnosti definuje události chcete zpracovat. Například nadřazený `Page` (bez `Click` události definované) můžete naslouchat události kliknutí na tlačítko přiřazením obslužnou rutinu atribut ve tvaru `Button.Click`. Ale `Handles` nepodporuje *typename.membername* formuláři, protože musí podporovat, konfliktní *Instance.Event* formuláře. Podrobnosti najdete v tématu [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 `Handles` obslužné rutiny, které jsou vyvolány pro události, které jsou již označena jako zpracovaná nelze připojit. Místo toho musíte použít kód a volání `handledEventsToo` přetížení z <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Nepoužívejte `Handles` syntaxe v kódu Visual Basic, když zadáte v jazyce XAML obslužné rutiny události pro jednu událost. Obslužné rutiny události v tomto případě je volána dvakrát.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak WPF implementuje "zpracovává" funkce  
 Při [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] se stránka kompiluje, deklaruje pomocný soubor `Friend` `WithEvents` odkazy na každý element na stránce, který má <xref:System.Windows.FrameworkContentElement.Name%2A> sada vlastností (nebo [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md) deklarovaný). Každá pojmenované instance je potenciálně element, jemuž lze přiřadit k obslužné rutině prostřednictvím `Handles`.  
  
> [!NOTE]
>  V rámci [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] zobrazit dokončení, pro které jsou k dispozici pro elementy `Handles` odkaz na stránce. Ale může to trvat jednu kompilaci průchodu tak, aby všechny pomocný soubor můžete zadat `Friends` odkazy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [Označení směrovaných událostí jako zpracovaných a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
