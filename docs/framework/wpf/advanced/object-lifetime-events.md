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
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141104"
---
# <a name="object-lifetime-events"></a>Události doby života objektu
Toto téma popisuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konkrétní události, které označují fáze životnosti objektu vytváření, použití a zničení.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a přečetli jste si téma Přehled [vlastností závislostí.](dependency-properties-overview.md) Chcete-li sledovat příklady v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (viz Přehled [XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>Události doby života objektu  
 Všechny objekty ve spravovaném kódu rozhraní Microsoft .NET Framework procházejí podobnou sadou fází života, vytváření, použití a ničení. Mnoho objektů má také fázi dokončení života, ke které dochází jako součást fáze zničení. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objekty, konkrétně vizuální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty, které identifikuje jako prvky, mají také sadu společných fází životnosti objektu. Programovací [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a aplikační modely vystavit tyto fáze jako řadu událostí. Existují čtyři hlavní typy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů s ohledem na události životnosti; prvky obecně, prvky okna, navigační hostitelé a aplikační objekty. Windows a navigační hostitelé jsou také v rámci větší seskupení vizuálních objektů (prvků). Toto téma popisuje události životnosti, které jsou společné pro všechny prvky a pak zavádí konkrétnější ty, které se vztahují k definicím aplikací, windows nebo navigační hostitelé.  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>Běžné celoživotní události pro prvky  
 Všechny wpf framework-level element (ty objekty <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>odvozené z jednoho <xref:System.Windows.FrameworkElement.Initialized>nebo <xref:System.Windows.FrameworkElement.Loaded>) <xref:System.Windows.FrameworkElement.Unloaded>má tři společné životnosti události: , , a .  
  
### <a name="initialized"></a>Inicializované  
 <xref:System.Windows.FrameworkElement.Initialized>je nejprve zvýšena a zhruba odpovídá inicializaci objektu voláním jeho konstruktoru. Vzhledem k tomu, že k události dochází v reakci na inicializaci, je zaručeno, že jsou nastaveny všechny vlastnosti objektu. (Výjimkou je použití výrazů, jako jsou dynamické prostředky nebo vazba; budou to nehodnocené výrazy.) V důsledku požadavku, že jsou nastaveny všechny <xref:System.Windows.FrameworkElement.Initialized> vlastnosti, se zdá, že se v pořadí nejprve ve stromu prvků vyskytuje posloupnost vnořených prvků, které jsou definovány v odznačovacím čísle, v pořadí podle nejhlubších prvků ve stromu elementů, potom nadřazených prvků směrem ke kořenovému adresáři. Toto pořadí je, protože nadřazený podřízený vztahy a uzavření jsou vlastnosti, a proto nadřazený nemůže hlásit inicializaci, dokud podřízené prvky, které vyplňují vlastnost jsou také zcela inicializovány.  
  
 Při psaní obslužné <xref:System.Windows.FrameworkElement.Initialized> rutiny v reakci na událost, je třeba vzít v úvahu, že neexistuje žádná záruka, že všechny ostatní prvky ve stromu elementu (logický strom nebo vizuální strom) kolem kde je připojen obslužná rutina, zejména nadřazené prvky. Členské proměnné mohou mít hodnotu null nebo zdroje dat ještě nemusí být naplněny základní vazbou (i na úrovni výrazu).  
  
### <a name="loaded"></a>Načten  
 <xref:System.Windows.FrameworkElement.Loaded>je aktivována další. Událost <xref:System.Windows.FrameworkElement.Loaded> je vyvolána před konečným vykreslováním, ale poté, co systém rozložení vypočítal všechny potřebné hodnoty pro vykreslování. <xref:System.Windows.FrameworkElement.Loaded>znamená, že logický strom, ve kterých je prvek obsažen, je dokončen a připojuje se ke zdroji prezentace, který poskytuje HWND a vykreslovací povrch. Standardní datové vazby (vazba na místní zdroje, jako jsou jiné <xref:System.Windows.FrameworkElement.Loaded>vlastnosti nebo přímo definované zdroje dat) dojde před . Mohlo dojít k asynchronní datové vazbě (externí nebo dynamické zdroje), ale podle definice její asynchronní povahy nelze zaručit, že došlo k ní.  
  
 Mechanismus, kterým <xref:System.Windows.FrameworkElement.Loaded> je vyvolána <xref:System.Windows.FrameworkElement.Initialized>událost se liší od . Událost <xref:System.Windows.FrameworkElement.Initialized> je aktivována prvek po elementu, bez přímé koordinace doplnění element stromu. Naproti tomu <xref:System.Windows.FrameworkElement.Loaded> událost je vyvolána jako koordinované úsilí v celém stromu elementu (konkrétně logického stromu). Když jsou všechny prvky ve stromu ve stavu, ve kterém jsou považovány za načtené, <xref:System.Windows.FrameworkElement.Loaded> událost je nejprve vyvolána na kořenový prvek. Událost <xref:System.Windows.FrameworkElement.Loaded> je pak aktivována postupně na každý podřízený prvek.  
  
> [!NOTE]
> Toto chování může povrchně podobat tunelové propojení pro směrované události. Žádné informace se však nepřenášejí z události na událost. Každý prvek má vždy možnost <xref:System.Windows.FrameworkElement.Loaded> zpracovat jeho událost a označení dat události jako zpracovány nemá žádný vliv mimo tento prvek.  
  
### <a name="unloaded"></a>uvolněné  
 <xref:System.Windows.FrameworkElement.Unloaded>je aktivována jako poslední a je inicionována odebráním zdroje prezentace nebo vizuálního nadřazeného objektu. Při <xref:System.Windows.FrameworkElement.Unloaded> vydnoceně a zpracování, prvek, který <xref:System.Windows.FrameworkElement.Parent%2A> je nadřazený zdroj události (jak je určeno vlastností) nebo jakýkoli daný prvek směrem nahoru v logické nebo vizuální stromy může již byly unset, což znamená, že datové vazby, odkazy na prostředky a styly nemusí být nastavena na jejich normální nebo poslední známé hodnotě běhu.  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>Prvky modelu aplikace doživotní události  
 V návaznosti na společné události životnosti prvků <xref:System.Windows.Application> <xref:System.Windows.Window>jsou <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationWindow>následující <xref:System.Windows.Controls.Frame>prvky modelu aplikace: , , , a . Ty rozšiřují společné události životnosti o další události, které jsou relevantní pro jejich konkrétní účel. Ty jsou podrobně popsány v následujících umístěních:  
  
- <xref:System.Windows.Application>: [Přehled správy aplikací](../app-development/application-management-overview.md).  
  
- <xref:System.Windows.Window>: [Přehled WPF Windows](../app-development/wpf-windows-overview.md).  
  
- <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>a <xref:System.Windows.Controls.Frame>: [Navigační přehled](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
