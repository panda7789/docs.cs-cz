---
title: Přehled topologií navigace
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 8976ba7973e4f53022846b98c47d5613fd6ba158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="navigation-topologies-overview"></a>Přehled topologií navigace
<a name="introduction"></a> Tento přehled obsahuje úvod do topologie navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tři běžné topologie navigační s ukázky, jsou následně popsané.  
  
> [!NOTE]
>  Než si přečtete v tomto tématu, měli byste se seznámit s ohledem na strukturovaných navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí stránky funkce. Další informace o obou těchto tématech najdete v tématu [strukturovaných navigační přehled](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Navigace topologie](#Navigation_Topologies)  
  
-   [Strukturované navigační topologie](#Structured_Navigation_Topologies)  
  
-   [Navigace přes pevné lineární topologie](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Dynamické navigační přes pevné hierarchické topologie](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Navigace v dynamicky generovaném topologie](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Navigace topologie  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigace se obvykle skládá z stránky (<xref:System.Windows.Controls.Page>) s hypertextové odkazy (<xref:System.Windows.Documents.Hyperlink>), přejděte k ostatním stránkám při kliknutí na. Jsou určeny stránek, které jsou přešli [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (viz [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)). Vezměte v úvahu následující jednoduchý příklad, který ukazuje stránky, hypertextové odkazy, a [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Tyto stránky jsou uspořádány do *navigační topologie* jejichž struktura je dáno jak přecházet mezi stránkami. Tato topologie konkrétní navigace je vhodná v jednoduchého scénáře, i když navigační může vyžadovat komplexnější topologie, některé z nich může být definovaný jenom když aplikace běží.  
  
 Toto téma popisuje tři běžné topologie navigace: *pevné lineární*, *pevné hierarchické*, a *dynamicky generovaném*. Každé navigační topologii se demonstruje vzorku, který má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako ten, který je znázorněno na následujícím obrázku:  
  
 ![Úloha stránky s datovými položkami](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Strukturované navigační topologie  
 Existují dva široké typy navigační topologie:  
  
-   **Pevné topologie**: definované při kompilaci a v době běhu se nemění. Opravené topologie jsou užitečné pro navigaci prostřednictvím pevné pořadí stránek v lineární nebo hierarchické pořadí.  
  
-   **Dynamické topologie**: definované v době běhu na základě informací, které jsou shromážděny od uživatele, aplikace nebo systému. Dynamické topologie je užitečný v případě stránky lze procházet v různých pořadí.  
  
 Přestože je možné vytvořit navigační topologie pomocí stránek, ukázky použít stránku funkce, protože poskytují další podporu, který zjednodušuje podporu pro předávání a vrací data prostřednictvím stránky topologie.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigace přes pevné lineární topologie  
 Pevné lineární topologie je podobná struktuře průvodce, který má jeden nebo více stránek průvodce, které jsou navigaci v pevné pořadí. Následující obrázek ukazuje základní strukturu a toku průvodce s pevnou lineární topologií.  
  
 ![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 Typické chování pro navigaci přes pevné lineární topologie zahrnují následující:  
  
-   Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce. Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí deníku.  
  
-   Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.  
  
-   Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
-   Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
-   Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
-   Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku. Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamické navigační přes pevné hierarchické topologie  
 V některých aplikacích stránky procházení do dvou nebo více dalších stránek, jak je znázorněno na následujícím obrázku.  
  
 ![Na stránce, který můžete přejít na více stránkách](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 Tato struktura je známý jako pevné hierarchické topologie a pořadí, ve kterém je provázán hierarchii je často dáno v době běhu aplikace nebo uživatele. Každé stránce v hierarchii, která umožňuje navigace na dvě nebo více stránek za běhu, shromažďuje data potřebná k určení stránku, která má přejděte do. Následující obrázek ukazuje jeden z několika možných navigační pořadí podle na předchozím obrázku.  
  
 ![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 Přestože v době běhu je určit pořadí, ve kterém jsou stránky v pevné hierarchická struktura navigaci, činnost koncového uživatele je stejný jako činnost koncového uživatele pro pevnou lineární topologie:  
  
-   Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce. Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí deníku.  
  
-   Uživatelé mohou změnit pořadí navigace, pokud jejich přejděte zpět prostřednictvím deníku.  
  
-   Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.  
  
-   Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
-   Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
-   Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
-   Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku. Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigace v dynamicky generovaném topologie  
 V některých aplikacích pořadí, ve kterém jsou dvě nebo více stránek navigaci dá pouze určit v době běhu pomocí uživatele, aplikace nebo externí data. Následující obrázek ukazuje sadu stránek se v neurčeném navigační sekvenci.  
  
 ![Diagram topologie pro navigační](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 Následující obrázek znázorňuje navigační pořadí, které jste vybrali uživatelem v době běhu.  
  
 ![Navigace – diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 Navigace pořadí se označuje jako dynamicky generovaném topologie. Pro uživatele jako s jiných topologiích navigační činnost koncového uživatele je stejný, jako je pro předchozí topologie:  
  
-   Navigace na stránce volání Spouštěče stránku, která inicializuje průvodce a přejde na první stránce průvodce. Na stránce Spouštěče ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-menší <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, však může zjednodušit inicializace průvodce, zvlášť pokud je komplexní inicializace.  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí zpět a předat dál tlačítka (nebo hypertextové odkazy).  
  
-   Uživatelé mohou přecházet mezi stránkami pomocí deníku.  
  
-   Uživatele můžete ukončit průvodce z kterékoli stránce průvodce klepnutím na tlačítko Storno.  
  
-   Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
-   Pokud zrušení průvodce Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
-   Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
-   Až průvodce dokončí (přijímat nebo došlo ke zrušení), stránek, které tvoří průvodce se odeberou z deníku. Díky tomu každou instanci Průvodce izolovaných, aby se předešlo potenciální data nebo anomálií stavu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Přehled strukturované navigace](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
