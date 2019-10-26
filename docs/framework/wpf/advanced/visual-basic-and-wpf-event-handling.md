---
title: Zpracování událostí v jazyku Visual Basic a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 12ced911c6fded5dd9016ea377a3a4518c9c2ee1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920343"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Zpracování událostí v jazyku Visual Basic a WPF
Pro jazyk Microsoft Visual Basic .NET konkrétně můžete použít klíčové slovo `Handles` pro konkrétní jazyk k přidružení obslužných rutin událostí k instancím namísto připojení obslužných rutin událostí k atributům nebo použití metody <xref:System.Windows.UIElement.AddHandler%2A>. Nicméně metoda `Handles` pro připojování obslužných rutin k instancím má určitá omezení, protože syntaxe `Handles` nepodporuje některé ze specifických funkcí směrovaných událostí systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="using-handles-in-a-wpf-application"></a>Použití "Handles" v aplikaci WPF  
 Obslužné rutiny událostí, které jsou připojeny k instancím a událostem `Handles` musí být definovány v rámci částečné deklarace třídy instance, což je také požadavek obslužných rutin události, které jsou přiřazeny prostřednictvím hodnot atributů u elementů. `Handles` lze zadat pouze pro element na stránce, která má hodnotu vlastnosti <xref:System.Windows.FrameworkContentElement.Name%2A> (nebo je deklarována [direktiva x:Name](../../xaml-services/x-name-directive.md) ). Důvodem je, že <xref:System.Windows.FrameworkContentElement.Name%2A> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vytvoří odkaz na instanci, který je nezbytný k podpoře *instance.* formát odkazu na událost vyžadovaný syntaxí `Handles`. Jediným prvkem, který lze použít pro `Handles` bez odkazu <xref:System.Windows.FrameworkContentElement.Name%2A> je instance kořenového prvku, která definuje částečnou třídu.  
  
 Můžete přiřadit stejnou obslužnou rutinu více prvků oddělením *instance.* odkazy na události po `Handles` čárkami.  
  
 Můžete použít `Handles` k přiřazení více než jedné obslužné rutiny stejné *instanci.* odkaz na událost. Nepřiřazujte žádné důležitosti k pořadí, ve kterém jsou obslužné rutiny uvedeny v odkazu `Handles`; je vhodné předpokládat, že obslužné rutiny, které zpracovávají stejnou událost, lze vyvolat v libovolném pořadí.  
  
 Chcete-li odebrat obslužnou rutinu, která byla přidána s `Handles` v deklaraci, můžete volat <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Můžete použít `Handles` k připojení obslužných rutin pro směrované události, pokud připojíte obslužné rutiny k instancím, které definují události zpracovávané v tabulkách členů. U směrovaných událostí obslužné rutiny, které jsou připojeny k `Handles`, dodržují stejná pravidla směrování jako obslužné rutiny, které jsou připojeny jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy, nebo se společným podpisem <xref:System.Windows.UIElement.AddHandler%2A>. To znamená, že pokud je již událost označena jako zpracovaná (vlastnost <xref:System.Windows.RoutedEventArgs.Handled%2A> v datech události je `True`), pak obslužné rutiny připojené pomocí `Handles` nejsou vyvolány v reakci na tuto instanci události. Událost může být označena jako zpracovaná obslužnými rutinami instance na jiném prvku v trase, nebo pomocí zpracování třídy buď na aktuálním prvku, nebo v předchozích prvcích podél trasy. Pro vstupní události, které podporují spárované tunelové/bublinové události, může tunelový postup označit, že se zpracoval pár událostí. Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Omezení popisovače pro přidání obslužných rutin  
 `Handles` nemůže odkazovat na obslužné rutiny pro připojené události. Pro tuto připojenou událost je nutné použít metodu přistupující objekt `add` nebo atributy události *typeName. EventName* v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podrobnosti najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 U směrovaných událostí můžete použít pouze `Handles` k přiřazení obslužných rutin pro instance, kde tato událost existuje v tabulce Členové instance. Nicméně s směrovanými událostmi obecně může být nadřazený element naslouchací proces pro událost z podřízených prvků, i když nadřazený prvek nemá tuto událost v tabulce členů. V syntaxi atributu lze tento atribut zadat prostřednictvím typu *typeName. Member* , který je v souladu s typem, který je ve skutečnosti definována událost, kterou chcete zpracovat. Například nadřazený `Page` (bez `Click` definované události) může naslouchat pro události kliknutí tlačítkem, a to přiřazením obslužné rutiny atributu ve formuláři `Button.Click`. Ale `Handles` nepodporuje tvar *typeName. Member* , protože musí podporovat konfliktní *instanci. formulář události* . Podrobnosti najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 `Handles` nemůže připojit obslužné rutiny, které jsou vyvolány pro události, které jsou již označeny jako zpracované. Místo toho je nutné použít kód a volat `handledEventsToo` přetížení <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
> Nepoužívejte syntaxi `Handles` v kódu Visual Basic při určení obslužné rutiny události pro stejnou událost v jazyce XAML. V tomto případě je obslužná rutina události volána dvakrát.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak WPF implementuje funkce Handles  
 Když je [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránka kompilována, zprostředkující soubor deklaruje `Friend` `WithEvents` odkazy na všechny prvky na stránce, které mají <xref:System.Windows.FrameworkContentElement.Name%2A> sadu vlastností (nebo deklarované [direktivy x:Name](../../xaml-services/x-name-directive.md) ). Každá pojmenovaná instance je potenciálně prvkem, který lze přiřadit k obslužné rutině prostřednictvím `Handles`.  
  
> [!NOTE]
> V rámci sady Visual Studio může IntelliSense zobrazit dokončení, pro které prvky jsou k dispozici pro `Handles` odkaz na stránku. To však může trvat jeden průchod kompilace, aby zprostředkující soubor mohl naplnit všechny `Friends` odkazy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
