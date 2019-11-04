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
ms.openlocfilehash: c0858a0194bc0e9efa60a42d4029bdba9f4f3fef
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458571"
---
# <a name="object-lifetime-events"></a>Události doby života objektu
Toto téma popisuje konkrétní události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], které signalizují fáze při vytváření, používání a ničení objektů v životním cyklu.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti na třídách [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a přečtěte si téma [Přehled vlastností závislosti](dependency-properties-overview.md) . Chcete-li postupovat podle příkladů v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (viz [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) a zjistit, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Události doby života objektu  
 Všechny objekty v Microsoft .NET Framework spravovaném kódu procházejí podobnou sadou fází života, vytváření, používání a zničení. Mnoho objektů má také finalizaci fáze životnosti, která se vyskytuje jako součást fáze zničení. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů přesněji řečeno vizuální objekty, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifikuje jako prvky, také mají sadu běžných fází životního cyklu objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování a aplikační modely zveřejňují tyto fáze jako řadu událostí. Existují čtyři hlavní typy objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s ohledem na události životního cyklu; prvky obecné, prvky okna, navigační hostitelé a objekty aplikace. Hostitelé systému Windows a navigace jsou také v rámci většího seskupení vizuálních objektů (elementy). Toto téma popisuje události životního cyklu, které jsou společné pro všechny prvky, a pak zavádí konkrétnější informace, které se vztahují na definice aplikací, Windows nebo navigační hostitele.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Běžné události životního cyklu pro prvky  
 Jakýkoli element na úrovni WPF Frameworku (objekty odvozené od <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má tři běžné události životního cyklu: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>a <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializované  
 Nejprve je vyvolána <xref:System.Windows.FrameworkElement.Initialized> a zhruba odpovídá inicializaci objektu voláním jeho konstruktoru. Vzhledem k tomu, že událost probíhá v reakci na inicializaci, je zaručeno, že jsou nastaveny všechny vlastnosti objektu. (Výjimka je použití výrazů, jako jsou dynamické prostředky nebo vazby; tyto výrazy budou nehodnocené.) V důsledku požadavku na nastavení všech vlastností je sekvence <xref:System.Windows.FrameworkElement.Initialized> vyvolána vnořenými prvky, které jsou definovány v kódu, se zobrazí ve stromové struktuře elementu jako první a potom nadřazené prvky do kořenového adresáře. Toto pořadí je způsobeno tím, že vztahy nadřazený-podřízený a zahrnutí jsou vlastnosti, a proto nadřazený objekt nemůže nahlásit inicializaci, dokud nebudou podřízené prvky, které tuto vlastnost naplní, zcela inicializovány.  
  
 Při psaní obslužných rutin v reakci na událost <xref:System.Windows.FrameworkElement.Initialized>, je nutné vzít v úvahu, že není nijak zaručeno, že všechny ostatní prvky ve stromové struktuře elementů (logický strom nebo vizuální strom), kde je obslužná rutina připojena, jsou vytvořeny, zejména nadřazené elementu. Členské proměnné mohou mít hodnotu null nebo zdroje dat ještě nemusí být naplněny základní vazbou (dokonce i na úrovni výrazu).  
  
### <a name="loaded"></a>Načten  
 <xref:System.Windows.FrameworkElement.Loaded> je vyvolána další. Událost <xref:System.Windows.FrameworkElement.Loaded> je aktivována před konečným vykreslováním, ale poté, co systém rozložení vypočítal všechny nezbytné hodnoty pro vykreslení. <xref:System.Windows.FrameworkElement.Loaded> znamená, že logický strom, v němž je element obsažen, je dokončen a je připojen ke zdroji prezentace, který poskytuje HWND a plochu vykreslování. Před <xref:System.Windows.FrameworkElement.Loaded>k dispozici je standardní datová vazba (vazba na místní zdroje, jako jsou další vlastnosti nebo přímo definované zdroje dat). Bylo možné, že došlo k asynchronní datové vazbě (externím nebo dynamickým zdrojům), ale podle definice její asynchronní povahy nelze zaručit, že došlo k jejímu selhání.  
  
 Mechanismus, pomocí kterého je vyvolána událost <xref:System.Windows.FrameworkElement.Loaded>, se liší od <xref:System.Windows.FrameworkElement.Initialized>. Událost <xref:System.Windows.FrameworkElement.Initialized> je vyvolána elementem elementem, bez přímé koordinace podle dokončeného stromu elementu. Naproti tomu <xref:System.Windows.FrameworkElement.Loaded> událost je vyvolána jako koordinovaný úsilí v celém stromu elementu (konkrétně logický strom). Pokud jsou všechny prvky ve stromové struktuře ve stavu, kde jsou považovány za načtenou, událost <xref:System.Windows.FrameworkElement.Loaded> je nejprve vyvolána u kořenového prvku. Událost <xref:System.Windows.FrameworkElement.Loaded> se pak postupně vyvolala u každého podřízeného prvku.  
  
> [!NOTE]
> Toto chování může vést k napodobení tunelu pro směrovanou událost. Z událostí na událost však nebudou přenášet žádné informace. Každý prvek má vždy možnost zpracovat událost <xref:System.Windows.FrameworkElement.Loaded> a označit data události jako zpracovaná, nemá žádný vliv na rámec tohoto prvku.  
  
### <a name="unloaded"></a>uvolněné  
 <xref:System.Windows.FrameworkElement.Unloaded> se vyvolalo jako poslední a iniciuje ho buď zdroj prezentace, nebo vizuální nadřazený prvek, který se odebírá. Když je vyvoláno a zpracováno <xref:System.Windows.FrameworkElement.Unloaded>, prvek, který je zdrojem události nadřazený (jak je určen vlastností <xref:System.Windows.FrameworkElement.Parent%2A>), nebo jakýkoli daný element směrem nahoru v logických nebo vizuálních stromech, pravděpodobně již byl nastaven, což znamená, že datová vazba, odkazy na prostředky a styly nemusí být nastavené na normální nebo poslední známou hodnotu za běhu.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Prvky aplikačního modelu události doby života  
 Vytváření na běžných událostech životního cyklu pro prvky jsou následující prvky modelu aplikace: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>a <xref:System.Windows.Controls.Frame>. Ty rozšíří běžné události životního cyklu s dalšími událostmi, které jsou relevantní pro jejich konkrétní účely. Tyto informace jsou podrobněji popsány v následujících umístěních:  
  
- <xref:System.Windows.Application>: [Přehled správy aplikací](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Přehled Windows WPF](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>a <xref:System.Windows.Controls.Frame>: [Přehled navigace](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Priorita hodnot vlastností závislosti](dependency-property-value-precedence.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
