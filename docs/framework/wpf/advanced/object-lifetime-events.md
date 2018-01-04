---
title: "Události doby života objektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81bd06811e428645a9a3103be457d30266a353c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="object-lifetime-events"></a>Události doby života objektu
Toto téma popisuje konkrétní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události, které označují fázích v životnost objektu vytvoření, použití a odstranění.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a mít ke čtení [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) tématu. Chcete-li v následujících příkladech v tomto tématu byste měli také porozumět [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (najdete v části [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)) a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Události doby života objektu  
 Všechny objekty v [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] spravovaného kódu projít podobnou sadu fázích životního, vytvoření, použití a odstranění. Mnoho objektů také mít fáze finalizace života, ke kterému dochází v rámci fáze odstraňování. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]objekty, další konkrétně visual objekty, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifikuje jako elementy, také obsahovat sadu běžné fázích životního objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Programovací a aplikace modely vystavit tyto fáze jako řady událostí. Existují čtyři hlavní typy objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s ohledem na události životního cyklu; prvky v obecné, prvků okna, navigace hostitelů a objekty aplikací. Hostitelé systému Windows a navigace jsou také v rámci větší seskupení vizuální objekty (prvky). Toto téma popisuje události životního cyklu, které jsou společné pro všechny elementy a pak zavádí konkrétnější ty, které platí pro definice aplikací, windows nebo navigační hostitele.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Běžné doba platnosti události pro elementy  
 Libovolný element úrovni rozhraní WPF (těchto objektů odvozování z buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má tři nejčastější události životního cyklu: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, a <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializované  
 <xref:System.Windows.FrameworkElement.Initialized>Nejprve se vyvolá a zhruba odpovídá inicializace objektu voláním jeho konstruktoru. Protože k této události dojde v reakci na inicializace, je zaručeno, že všechny vlastnosti objektu jsou nastaveny. (Výjimkou je výraz použití, jako je dynamická prostředky nebo vazby, budou tyto unevaluated výrazy.) V důsledku požadavku, že všechny vlastnosti jsou nastavená, pořadí <xref:System.Windows.FrameworkElement.Initialized> vyvolaných ve vnořených elementů, které jsou definovány v značek pravděpodobně dojde v pořadí nejhlubší elementů ve stromové struktuře element nejprve pak nadřazených elementů směrem k kořenu. Pořadí je protože vztahů nadřazenosti a podřízenosti a členství ve skupině jsou vlastnosti, a proto nelze nadřazené sestavy inicializace dokud podřízené prvky, které vyplnění vlastnost jsou také zcela inicializován.  
  
 Když píšete obslužné rutiny v reakci <xref:System.Windows.FrameworkElement.Initialized> událostí, musíte zvážit, zda není zaručeno, že všechny elementy ve stromové struktuře – element (logického stromu nebo vizuálním stromu) kolem kterému je připojena obslužná rutina byly vytvořeny, zejména nadřazené elementy. Členské proměnné může mít hodnotu null, nebo zdroje dat nemusí být ještě naplněno základní vazbou (i na úrovni výrazu).  
  
### <a name="loaded"></a>Načten  
 <xref:System.Windows.FrameworkElement.Loaded>je vyvolána Další. <xref:System.Windows.FrameworkElement.Loaded> Událost se vyvolá, před posledním vykreslování, ale po rozložení systému obsahuje počítané všechny nezbytné hodnoty pro vykreslování. <xref:System.Windows.FrameworkElement.Loaded>má za následek, že logické stromové struktury, která je součástí element dokončení a připojuje ke zdroji prezentace, které poskytuje HWND a prostor pro vykreslování. Standardní datová vazba (vazbu na místní zdrojů, například jinými vlastnostmi nebo přímo definované datové zdroje) bude mít došlo k chybě před <xref:System.Windows.FrameworkElement.Loaded>. Asynchronní datová vazba (externí nebo dynamické zdrojů) může dojít, ale podle definice jeho asynchronní povahy nemůže zaručit do mají došlo k chybě.  
  
 Tento mechanismus, pomocí kterého <xref:System.Windows.FrameworkElement.Loaded> událost se vyvolá, se liší od <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Událostí je vyvolané element elementem bez přímé koordinace v rámci stromu dokončené elementu. Naopak <xref:System.Windows.FrameworkElement.Loaded> událost se vyvolá jako koordinovaný proces v rámci stromu celý elementu (konkrétně logického stromu). Pokud jsou všechny elementy ve stromové struktuře ve stavu, kde jsou považovány za načíst, <xref:System.Windows.FrameworkElement.Loaded> událost se vyvolá, nejprve v kořenovém elementu. <xref:System.Windows.FrameworkElement.Loaded> Se pak událost postupně na každý podřízený element.  
  
> [!NOTE]
>  Toto chování může vypadat na první pohled tunelové propojení pro směrované události. Žádné informace však probíhá události z události. Každý prvek má vždy možnost zpracování jeho <xref:System.Windows.FrameworkElement.Loaded> událostí a označí data události, jako zpracování nemá žádný vliv nad rámec tohoto prvku.  
  
### <a name="unloaded"></a>Není načten  
 <xref:System.Windows.FrameworkElement.Unloaded>je vyvolána naposledy a inicializuje zdroji prezentace nebo visual nadřazené se odebírá. Když <xref:System.Windows.FrameworkElement.Unloaded> je vyvolána a zpracovává elementu, který je nadřazený zdroj událostí (počítáno od <xref:System.Windows.FrameworkElement.Parent%2A> vlastnost) nebo všechny daného elementu směrem nahoru v stromy logickou nebo visual již bylo zrušeno nastavení, což znamená, že datovou vazbu, odkazy na prostředek , a styly nemusí být nastavena na jejich normální nebo poslední známá hodnota doby běhu.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Prvky modelu aplikace události životního cyklu  
 Vytváření na běžné doba platnosti události pro prvky jsou následující prvky modelu aplikace: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.Frame>. Tyto rozšířit běžné události životního cyklu s další události, které jsou relevantní pro jejich konkrétní účel. Tyto jsou podrobněji v následujících umístěních:  
  
-   <xref:System.Windows.Application>: [Přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [WPF ve Windows – přehled](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.Frame>: [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Priorita hodnot vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
