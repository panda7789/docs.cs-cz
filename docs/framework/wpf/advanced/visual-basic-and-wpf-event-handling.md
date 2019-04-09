---
title: Zpracování událostí v jazyku Visual Basic a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: c6e1863850ebf04408c7ffc7b784e9ca3ca12cf5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078015"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Zpracování událostí v jazyku Visual Basic a WPF
Pro jazyk Microsoft Visual Basic .NET, můžete použít konkrétní jazyk `Handles` – klíčové slovo k přidružení obslužné rutiny události instance, místo připojování obslužné rutiny události s atributy nebo použití <xref:System.Windows.UIElement.AddHandler%2A> metody. Ale `Handles` techniku pro připojení k instancím obslužných rutin mají určitá omezení, protože `Handles` syntaxe nemůže zajišťovat podporu pro některé funkce konkrétní směrované události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí.  
  
## <a name="using-handles-in-a-wpf-application"></a>Použití "Popisovače" v aplikaci WPF  
 Obslužné rutiny událostí, které jsou připojené k instancí a událostí pomocí `Handles` musí všechny definovat v deklaraci částečné třídy instance, která je také požadavek pro obslužné rutiny událostí, které jsou přiřazeny prostřednictvím hodnoty atributů na prvky. Můžete zadat jenom `Handles` pro element na stránce, která má <xref:System.Windows.FrameworkContentElement.Name%2A> hodnotu vlastnosti (nebo [x: Name – direktiva](../../xaml-services/x-name-directive.md) deklarovaná). Důvodem je, že <xref:System.Windows.FrameworkContentElement.Name%2A> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vytvoří instanci odkaz, který je nezbytný pro podporu *Instance.Event* vyžadované formát reference `Handles` syntaxe. Jediným prvkem, který lze použít pro `Handles` bez <xref:System.Windows.FrameworkContentElement.Name%2A> odkaz je instance kořenový element, který definuje částečné třídy.  
  
 Můžete přiřadit stejnou obslužnou rutinu více prvků tak, že oddělíte *Instance.Event* odkazuje po `Handles` čárkami.  
  
 Můžete použít `Handles` přiřadit více než jednu obslužnou rutinu na stejný *Instance.Event*odkaz. Nepřiřazujte všechny důležité pořadí, ve kterém jsou uvedeny obslužných rutin v `Handles` odkazovat; byste měli předpokládat, že obslužné rutiny, které zpracovávají stejnou událost může být vyvolána v libovolném pořadí.  
  
 Chcete-li odebrat obslužnou rutinu, která byla přidána s `Handles` v deklaraci, můžete volat <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Můžete použít `Handles` připojit obslužné rutiny pro směrované události, tak dlouho, dokud obslužné rutiny připojit k instancím, které definují zpracovává události v tabulkách jejich členy. Směrované události, obslužné rutiny, které jsou připojené pomocí `Handles` postupujte podle stejných pravidel směrování, stejně jako obslužné rutiny, které jsou připojené jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy, nebo pomocí běžných podpis <xref:System.Windows.UIElement.AddHandler%2A>. To znamená, že pokud je již označena zpracované události ( <xref:System.Windows.RoutedEventArgs.Handled%2A> vlastnost v datech událostí je `True`), a připojil se k němu obslužné rutiny `Handles` nejsou vyvolány v reakci na tuto instanci události. Události lze označit jako zpracované instance obslužné rutiny na jiný element v trase, nebo zpracování buď na aktuální prvek nebo nemusí předchozí prvky na trase třídy. Pro vstupní události, které podporují spárované tunelového propojení/bubliny událostí může tunelového propojení směrování označili pár událost zpracovává. Další informace o směrované události najdete v tématu [směrovat Přehled událostí](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Omezení "Popisovače" pro přidání obslužné rutiny  
 `Handles` obslužné rutiny pro připojené události nelze odkazovat. Je nutné použít `add` přístupové metody pro tuto událost pro připojené, nebo *typename.eventname* události atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podrobnosti najdete v tématu [směrovat Přehled událostí](routed-events-overview.md).  
  
 Pro směrovaných událostí, lze použít pouze `Handles` přiřadit obslužné rutiny pro instance, kde existuje tuto událost v tabulce členů instance. Ale za použití směrovaných událostí obecně platí, nadřazený element může být naslouchacího procesu pro událost z podřízených prvků, i v případě, že nadřazený element nemá tuto událost v tabulce jeho členů. V syntaxi atributu, můžete určit to prostřednictvím *typename.membername* atribut formulář, který kvalifikuje typů, které se definuje skutečně vy chcete zpracovávat události. Například nadřazené `Page` (bez `Click` události definované) můžete očekávat události kliknutí na tlačítko přiřazením obslužnou rutinu atributu ve formuláři `Button.Click`. Ale `Handles` nepodporuje *typename.membername* formuláře, protože musí podporovat konfliktní *Instance.Event* formuláře. Podrobnosti najdete v tématu [směrovat Přehled událostí](routed-events-overview.md).  
  
 `Handles` obslužné rutiny, které jsou vyvolány události, které jsou označeny už zpracované nelze připojit. Místo toho je nutné použít kód a volání `handledEventsToo` přetížení <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Nepoužívejte `Handles` syntaxe v kódu jazyka Visual Basic, když zadáte obslužnou rutinu události pro stejnou událost v XAML. V tomto případě obslužná rutina události je volána dvakrát.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Způsob, jakým implementuje WPF "zpracovává" funkce  
 Při [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] je stránka kompilovaná, deklaruje pomocný soubor `Friend` `WithEvents` odkazy na každý prvek na stránce, která má <xref:System.Windows.FrameworkContentElement.Name%2A> nastavenou vlastnost (nebo [x: Name – direktiva](../../xaml-services/x-name-directive.md) deklarovaná). Každá pojmenované instance je potenciálně element, jemuž lze přiřadit k obslužné rutině prostřednictvím `Handles`.  
  
> [!NOTE]
>  V rámci [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] zobrazit dokončení pro které jsou k dispozici pro prvky `Handles` odkazu na stránce. Ale může to trvat kompilace najednou tak, aby všechny zprostředkující soubor můžete zadat `Friends` odkazy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
