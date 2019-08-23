---
title: Události doby života objektu
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933493"
---
# <a name="object-lifetime-events"></a>Události doby života objektu
Toto téma popisuje konkrétní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události, které signalizují fáze životního cyklu vytváření, používání a zničení objektů.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a přečetli jste si přehled o [vlastnostech závislosti](dependency-properties-overview.md) v tématu. Aby bylo možné postupovat podle příkladů v tomto tématu, měli byste také [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pochopit (viz [XAML Overview (WPF)](xaml-overview-wpf.md)) a vědět, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] psát aplikace.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Události doby života objektu  
 Všechny objekty v Microsoft .NET Framework spravovaném kódu procházejí podobnou sadou fází života, vytváření, používání a zničení. Mnoho objektů má také finalizaci fáze životnosti, která se vyskytuje jako součást fáze zničení. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objekty, přesněji řečeno, vizuální objekty, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které identifikují jako prvky, mají také sadu běžných fází životního cyklu objektu. Modely [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování a aplikací zpřístupňují tyto fáze jako řadu událostí. Existují čtyři hlavní typy objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] souvislosti s událostmi životního cyklu; prvky obecně, prvky okna, navigační hostitelé a objekty aplikace. Hostitelé systému Windows a navigace jsou také v rámci většího seskupení vizuálních objektů (elementy). Toto téma popisuje události životního cyklu, které jsou společné pro všechny prvky, a pak zavádí konkrétnější informace, které se vztahují na definice aplikací, Windows nebo navigační hostitele.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Běžné události životního cyklu pro prvky  
 Jakýkoli element na úrovni WPF Framework (objekty odvozené z <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má tři běžné události životního cyklu: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>a <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializované  
 <xref:System.Windows.FrameworkElement.Initialized>je aktivována jako první a zhruba odpovídá inicializaci objektu voláním jeho konstruktoru. Vzhledem k tomu, že událost probíhá v reakci na inicializaci, je zaručeno, že jsou nastaveny všechny vlastnosti objektu. (Výjimka je použití výrazů, jako jsou dynamické prostředky nebo vazby; tyto výrazy budou nehodnocené.) V důsledku požadavku na nastavení všech vlastností se pořadí <xref:System.Windows.FrameworkElement.Initialized> vystavení pomocí vnořených prvků, které jsou definovány v kódu, zobrazuje jako první v pořadí prvků ve stromu prvků, poté nadřazené prvky do kořenového adresáře. Toto pořadí je způsobeno tím, že vztahy nadřazený-podřízený a zahrnutí jsou vlastnosti, a proto nadřazený objekt nemůže nahlásit inicializaci, dokud nebudou podřízené prvky, které tuto vlastnost naplní, zcela inicializovány.  
  
 Při psaní obslužných rutin v reakci na <xref:System.Windows.FrameworkElement.Initialized> událost je nutné vzít v úvahu, že není nijak zaručeno, aby všechny ostatní prvky ve stromové struktuře elementů (logický strom nebo vizuální strom) kolem toho, kde je obslužná rutina připojena, byly vytvořeny, zejména nadřazené elementy. Členské proměnné mohou mít hodnotu null nebo zdroje dat ještě nemusí být naplněny základní vazbou (dokonce i na úrovni výrazu).  
  
### <a name="loaded"></a>Načten  
 <xref:System.Windows.FrameworkElement.Loaded>je vyvolána další. <xref:System.Windows.FrameworkElement.Loaded> Událost je aktivována před konečným vykreslováním, ale poté, co systém rozložení vypočítal všechny nezbytné hodnoty pro vykreslení. <xref:System.Windows.FrameworkElement.Loaded>má za následek, že logický strom, v němž je element obsažen, je dokončen a připojen ke zdroji prezentace, který poskytuje HWND a plochu vykreslování. Standardní datová vazba (vazba na místní zdroje, jako jsou například jiné vlastnosti nebo přímo definované zdroje dat) bude k dispozici <xref:System.Windows.FrameworkElement.Loaded>před. Bylo možné, že došlo k asynchronní datové vazbě (externím nebo dynamickým zdrojům), ale podle definice její asynchronní povahy nelze zaručit, že došlo k jejímu selhání.  
  
 Mechanismus, pomocí kterého je <xref:System.Windows.FrameworkElement.Loaded> událost vyvolána, se liší od <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Událost je vyvolána element podle elementu bez přímé koordinace podle dokončeného stromu elementu. Naproti tomu <xref:System.Windows.FrameworkElement.Loaded> je událost vyvolána jako koordinovaný úsilí v celém stromu elementu (konkrétně logický strom). Pokud jsou všechny prvky ve stromové struktuře ve stavu, kde jsou považovány za načtené, <xref:System.Windows.FrameworkElement.Loaded> událost je nejprve vyvolána u kořenového prvku. <xref:System.Windows.FrameworkElement.Loaded> Událost je pak postupně vyvolána na každém podřízeném elementu.  
  
> [!NOTE]
> Toto chování může vést k napodobení tunelu pro směrovanou událost. Z událostí na událost však nebudou přenášet žádné informace. Každý prvek má vždy příležitost zpracovat jeho <xref:System.Windows.FrameworkElement.Loaded> událost a označit data události jako zpracované nemá žádný vliv na rámec tohoto prvku.  
  
### <a name="unloaded"></a>uvolněné  
 <xref:System.Windows.FrameworkElement.Unloaded>je vyvolána jako poslední a je iniciována buď zdrojem prezentace, nebo s odebraným vizuálním nadřazeným objektem. Když <xref:System.Windows.FrameworkElement.Unloaded> je vyvolána a zpracována, prvek, který je zdrojem událostí nadřazeným objektem ( <xref:System.Windows.FrameworkElement.Parent%2A> jak je určeno vlastností) nebo jakýmkoli daným prvkem směrem nahoru v logických nebo vizuálních stromech, pravděpodobně již byl nastaven, což znamená, že datová vazba, odkazy na prostředky a styly nemůžou být nastavené na normální nebo poslední známou hodnotu běhového běhu.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Prvky aplikačního modelu události doby života  
 Vytváření na běžných událostech životního cyklu pro prvky jsou následující prvky modelu aplikace <xref:System.Windows.Application>: <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.Frame>. Ty rozšíří běžné události životního cyklu s dalšími událostmi, které jsou relevantní pro jejich konkrétní účely. Tyto informace jsou podrobněji popsány v následujících umístěních:  
  
- <xref:System.Windows.Application>: [Přehled správy aplikací](../app-development/application-management-overview.md)  
  
- <xref:System.Windows.Window>: [Přehled Windows WPF](../app-development/wpf-windows-overview.md)  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>a :<xref:System.Windows.Controls.Frame> [Přehled navigace](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Priorita hodnot vlastností závislosti](dependency-property-value-precedence.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
