---
title: Zpracování událostí v jazyku Visual Basic a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 8407958ec76be7e402025ece57371e67581e5291
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942118"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Zpracování událostí v jazyku Visual Basic a WPF
Pro jazyk Microsoft Visual Basic .NET konkrétně můžete použít klíčové slovo specifické `Handles` pro přidružení obslužných rutin událostí k instancím namísto připojení obslužných rutin událostí s atributy nebo <xref:System.Windows.UIElement.AddHandler%2A> pomocí metody. Technika připojení obslužných rutin k instancím ale má určitá omezení, `Handles` protože syntaxe nepodporuje některé konkrétní funkce směrované události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému událostí. `Handles`  
  
## <a name="using-handles-in-a-wpf-application"></a>Použití "Handles" v aplikaci WPF  
 Obslužné rutiny událostí, které jsou připojeny k instancím `Handles` a událostem, musí být definovány v rámci částečné deklarace třídy instance, což je také požadavek obslužných rutin událostí, které jsou přiřazeny prostřednictvím hodnot atributů u elementů. Můžete zadat `Handles` pouze pro element na stránce, která <xref:System.Windows.FrameworkContentElement.Name%2A> má hodnotu vlastnosti (nebo je deklarována [direktiva x:Name](../../xaml-services/x-name-directive.md) ). Důvodem je, že <xref:System.Windows.FrameworkContentElement.Name%2A> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v vytvoří odkaz na instanci, který je nezbytný pro podporu *instance.* formát odkazu na `Handles` událost vyžadovaný syntaxí. Jediným prvkem, který lze použít pro `Handles` <xref:System.Windows.FrameworkContentElement.Name%2A> bez odkazu je instance kořenového elementu, která definuje částečnou třídu.  
  
 Můžete přiřadit stejnou obslužnou rutinu více prvků oddělením *instance.* odkazy na události za `Handles` čárkami.  
  
 Můžete použít `Handles` k přiřazení více než jedné obslužné rutiny stejné *instanci.* odkaz na událost. Nepřiřazujte žádné důležité pořadí, ve kterém jsou obslužné rutiny uvedeny v `Handles` odkazu. měli byste předpokládat, že obslužné rutiny, které zpracovávají stejnou událost, mohou být vyvolány v libovolném pořadí.  
  
 Chcete-li odebrat obslužnou rutinu, `Handles` která byla přidána s v deklaraci <xref:System.Windows.UIElement.RemoveHandler%2A>, můžete zavolat.  
  
 Můžete použít `Handles` k připojení obslužných rutin pro směrované události, pokud připojíte obslužné rutiny k instancím, které definují událost zpracovávaná v tabulkách členů. U směrovaných událostí obslužné rutiny, které `Handles` jsou připojeny se stejným pravidlem směrování jako obslužné rutiny, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které jsou připojeny jako atributy, nebo <xref:System.Windows.UIElement.AddHandler%2A>se společným podpisem. To znamená, že pokud je již událost označena jako zpracovaná <xref:System.Windows.RoutedEventArgs.Handled%2A> (vlastnost v datech události je `True`) `Handles` , pak obslužné rutiny, které jsou připojeny, nejsou vyvolány v reakci na tuto instanci události. Událost může být označena jako zpracovaná obslužnými rutinami instance na jiném prvku v trase, nebo pomocí zpracování třídy buď na aktuálním prvku, nebo v předchozích prvcích podél trasy. Pro vstupní události, které podporují spárované tunelové/bublinové události, může tunelový postup označit, že se zpracoval pár událostí. Další informace o směrovaných událostech najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Omezení popisovače pro přidání obslužných rutin  
 `Handles`nelze odkazovat na obslužné rutiny pro připojené události. Je nutné použít `add` metodu přistupující k této připojené události nebo atributy události *typeName. EventName* v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Podrobnosti najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 U směrovaných událostí můžete použít `Handles` pouze k přiřazení obslužných rutin pro instance, kde tato událost existuje v tabulce Členové instance. Nicméně s směrovanými událostmi obecně může být nadřazený element naslouchací proces pro událost z podřízených prvků, i když nadřazený prvek nemá tuto událost v tabulce členů. V syntaxi atributu lze tento atribut zadat prostřednictvím typu *typeName. Member* , který je v souladu s typem, který je ve skutečnosti definována událost, kterou chcete zpracovat. Například nadřazený `Page` objekt (bez `Click` definované události) může naslouchat pro události kliknutí tlačítkem pomocí přiřazení obslužné rutiny atributu ve formuláři `Button.Click`. Ale `Handles` nepodporuje tvar *typeName. Member* , protože musí podporovat konfliktní *instanci. formulář události* . Podrobnosti najdete v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
 `Handles`nelze připojit obslužné rutiny, které jsou vyvolány pro události, které jsou již označeny jako zpracované. Místo toho je nutné použít kód a volat `handledEventsToo` <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>přetížení.  
  
> [!NOTE]
> Nepoužívejte `Handles` syntaxi v Visual Basic kódu při určení obslužné rutiny události pro stejnou událost v jazyce XAML. V tomto případě je obslužná rutina události volána dvakrát.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak WPF implementuje funkce Handles  
 `Friend` [](../../xaml-services/x-name-directive.md) <xref:System.Windows.FrameworkContentElement.Name%2A> Při kompilaci `WithEvents` stránky zprostředkující soubor deklaruje odkazy na každý element na stránce, která má sadu vlastností deklarovanou (nebo deklarovaná direktiva x:Name). [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Každá pojmenovaná instance je potenciálně prvkem, který lze přiřadit obslužné rutině `Handles`prostřednictvím.  
  
> [!NOTE]
> V [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]rámci může IntelliSense zobrazit dokončení, pro které prvky jsou k dispozici `Handles` pro odkaz na stránce. To však může trvat jeden průchod kompilace, aby mezisoubor mohl naplnit všechny `Friends` odkazy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
