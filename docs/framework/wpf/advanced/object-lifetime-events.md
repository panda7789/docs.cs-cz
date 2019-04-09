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
ms.openlocfilehash: 8ecc3f716061dfd08ac95652d1a9d8e06e26d949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175788"
---
# <a name="object-lifetime-events"></a>Události doby života objektu
Toto téma popisuje konkrétní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události, které místo fází v doba života objektu vytvoření, použití a zničení.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a čtení [přehled vlastností závislosti](dependency-properties-overview.md) tématu. Pokud chcete postupovat podle příkladů v tomto tématu, měli byste také znát [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (naleznete v tématu [přehled XAML (WPF)](xaml-overview-wpf.md)) a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>Události doby života objektu  
 Všechny objekty v kódu rozhraní Microsoft .NET Framework spravované projít podobnou sadu fáze života, vytváření, používání a zničení. Mnoho objektů má také dokončení fáze životnosti, ke které dochází v rámci fáze zničení. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty, další konkrétně vizuál objekty, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] identifikuje jako prvky, také mít sadu běžných fázích životnosti objektu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ukazují modely programování a aplikační těchto fází jako řady událostí. Existují čtyři hlavní typy objektů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s ohledem na životnost události; prvky v obecné, prvků, hostitel pro navigaci a objekty aplikací. Windows a navigace hostitelé jsou také v rámci větší seskupení vizuální objekty (prvky). Toto téma popisuje životnost události, které jsou společné pro všechny prvky a potom zavádí konkrétnější ty, které se vztahují k definice aplikací, windows nebo hostitel pro navigaci.  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>Běžné události doby života pro elementy  
 Libovolný prvek úrovni rozhraní WPF (tyto objekty odvozený od buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má tři běžné události doby života: <xref:System.Windows.FrameworkElement.Initialized>, <xref:System.Windows.FrameworkElement.Loaded>, a <xref:System.Windows.FrameworkElement.Unloaded>.  
  
### <a name="initialized"></a>Inicializované  
 <xref:System.Windows.FrameworkElement.Initialized> je nejprve vyvolána a zhruba odpovídá inicializace objektu voláním konstruktoru. Protože k této události dojde v reakci na inicializaci, zaručuje, že všechny vlastnosti objektu jsou nastaveny. (Výjimkou je použití výrazu, jako je dynamická prostředky nebo vazbu; to budou nevyhodnoceném výrazů.) V důsledku požadavku, že jsou nastavené všechny vlastnosti, pořadí <xref:System.Windows.FrameworkElement.Initialized> vyvolaných ve vnořené elementy, které jsou definovány v kódu se zobrazí nejprve vyskytuje v pořadí prvků nejhlubší ve stromu elementů pak nadřazené prvky směrem ke kořenu. Toto pořadí totiž vztahů nadřazenosti a podřízenosti a členství ve skupině jsou vlastnosti, a proto nadřazené nejde hlásit inicializace, dokud jsou podřízené prvky, které vyplnit vlastnost také zcela inicializován.  
  
 Když vytváříte obslužné rutiny v reakci <xref:System.Windows.FrameworkElement.Initialized> událost, musíte zvážit, že neexistuje žádná záruka, že všechny prvky v stromem prvků (Logická stromová struktura nebo vizuální strom) kolem kde je obslužná rutina připojená byly vytvořeny, zejména nadřazené prvky. Proměnné členů může mít hodnotu null, ani zdroje dat nemusí být ještě naplnit základní vazbou (i na úrovni výrazu).  
  
### <a name="loaded"></a>Načten  
 <xref:System.Windows.FrameworkElement.Loaded> je aktivována dále. <xref:System.Windows.FrameworkElement.Loaded> Událost je aktivována před konečného vykreslení, ale po systém rozložení vypočítal všechny potřebné hodnoty pro vykreslování. <xref:System.Windows.FrameworkElement.Loaded> zahrnuje, logického stromu, který je součástí element je kompletní a připojuje ke zdroji prezentace, které poskytuje HWND a vykreslovací plochu. Standardní datová vazba (vazby do místních zdrojů, jako ostatní vlastnosti nebo přímo definovaných zdrojů dat) budou došlo před <xref:System.Windows.FrameworkElement.Loaded>. Asynchronní datové vazby (externí nebo dynamické zdrojů) mohly nastat, ale podle definice jejich povaze asynchronní nelze zaručit, k nimž došlo.  
  
 Mechanismus, pomocí kterého <xref:System.Windows.FrameworkElement.Loaded> událost se vyvolá, se liší od <xref:System.Windows.FrameworkElement.Initialized>. <xref:System.Windows.FrameworkElement.Initialized> Událost je vyvolána element elementem bez přímé koordinace stromem dokončené element. Oproti tomu <xref:System.Windows.FrameworkElement.Loaded> událost se vyvolá jako koordinovaný proces v celém celý prvek stromu (konkrétně logického stromu). Pokud jsou všechny prvky ve stromové struktuře ve stavu, ve kterém jsou považovány za načtení <xref:System.Windows.FrameworkElement.Loaded> v kořenovém elementu je nejprve vyvolána událost. <xref:System.Windows.FrameworkElement.Loaded> Událost je pak postupně vyvolá na každý podřízený prvek.  
  
> [!NOTE]
>  Toto chování může vypadat na první pohled tunelové propojení pro směrovanou událost. Však žádné informace o provádění události z události. Každý prvek má vždy zpracovat jeho <xref:System.Windows.FrameworkElement.Loaded> událostí a označování dat události jako zpracované nemá žádný vliv nad rámec tohoto prvku.  
  
### <a name="unloaded"></a>uvolněné  
 <xref:System.Windows.FrameworkElement.Unloaded> je vyvolána jako poslední a inicializuje zdroji prezentace nebo vizuální nadřazený odebírá. Když <xref:System.Windows.FrameworkElement.Unloaded> se vyvolá a zpracovat elementu, který je nadřazený zdroj událostí (počítáno od <xref:System.Windows.FrameworkElement.Parent%2A> vlastnost) nebo libovolný daný prvek nahoru v stromů logické nebo visual již bylo zrušeno nastavení, což znamená, že vazba dat, odkazy na prostředky , a styly nemůže být nastavený na jejich normální nebo poslední známé hodnota doby běhu.  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>Prvky modelu aplikace události životního cyklu  
 Stavíme na běžné události doby života pro prvky jsou prvky modelu následující aplikace: <xref:System.Windows.Application>, <xref:System.Windows.Window>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.Frame>. Toto rozšíření běžné události doby života s další události, které jsou relevantní pro jejich konkrétní účel. Ty jsou podrobně popsány v následujících umístěních:  
  
-   <xref:System.Windows.Application>: [Přehled správy aplikací](../app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [Přehled WPF Windows](../app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.Frame>: [Přehled navigace](../app-development/navigation-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
