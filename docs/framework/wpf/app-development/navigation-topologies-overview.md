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
ms.openlocfilehash: 716cfbe7d12ccc2233d018f0346f84cf2fc5e733
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794641"
---
# <a name="navigation-topologies-overview"></a>Přehled topologií navigace
<a name="introduction"></a> Tento přehled poskytuje úvod do topologie navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Tři běžné topologie navigace s ukázkami, následně jsou popsány.  
  
> [!NOTE]
>  Před čtením tohoto tématu, měli byste se seznámit s konceptem strukturované navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí stránky funkce. Další informace o obou těchto tématech najdete v tématu [přehled strukturované navigace](structured-navigation-overview.md).  
  
 Toto téma obsahuje následující oddíly:  
  
- [Topologie navigace](#Navigation_Topologies)  
  
- [Topologie strukturované navigace](#Structured_Navigation_Topologies)  
  
- [Navigace prostřednictvím pevná lineární topologie](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Dynamické navigace přes pevná hierarchická topologie](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Navigace v dynamicky generovaném topologie](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie navigace  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigace se obvykle skládá z stránky (<xref:System.Windows.Controls.Page>) s hypertextovými odkazy (<xref:System.Windows.Documents.Hyperlink>), přejděte na jinou stránku po kliknutí. Stránky, které se přejde poté, jsou identifikované [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (viz [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md)). Vezměte v úvahu následující jednoduchý příklad, který zobrazí stránky, hypertextové odkazy, a [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Tyto stránky jsou uspořádány *topologie navigace* jehož struktura je určen jak přecházet mezi stránkami. Tato topologie konkrétní navigace je vhodný v jednoduché scénáře, i když navigace mohou vyžadovat složitější topologie, některé z nich je možné definovat jenom při spuštění aplikace.  
  
 Toto téma popisuje tři běžné topologie navigace: *pevná lineární*, *pevná hierarchická*, a *dynamicky generované*. Každá topologie navigace je znázorněn s pomocí ukázky, která má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jako je ten, který je znázorněno na následujícím obrázku:  
  
 ![Stránky úloh s datovými položkami a navigačních tlačítek.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologie strukturované navigace  
 Existují dva široké typy topologie navigace:  
  
- **Opraveno Topology**: definovaná v době kompilace a za běhu se nemění. Oprava topologie jsou užitečné pro navigaci pevné pořadí stránek v lineární nebo hierarchickém pořadí.  
  
- **Dynamické topologie**: definovaný v době běhu na základě vstupu, shromážděných od uživatele, aplikace nebo systému. Dynamické topologie jsou užitečné, pokud stránky se dá Navigovat v různých řad.  
  
 I když je možné vytvářet topologie navigace pomocí stránek, ukázky funkcí stránky použít, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vrací data na stránkách topologie.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigace prostřednictvím pevná lineární topologie  
 Pevná lineární topologie se podobá struktuře průvodce, který má jeden nebo více stránkách průvodce, které se přejde poté, v pevné posloupnosti. Následující obrázek znázorňuje základní strukturu a tok průvodce s pevná lineární topologie:  
  
 ![Diagram zobrazující průběh pevná lineární topologie.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Chování typické pro navigaci přes pevná lineární topologie patří:  
  
- Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce. Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.  
  
- Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).  
  
- Uživatelé můžou přecházet mezi stránky s využitím deníku.  
  
- Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.  
  
- Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
- Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
- Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku. Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamické navigace přes pevná hierarchická topologie  
 V některých aplikacích stránky povolit navigaci na dvě nebo více stránek, jak je znázorněno na následujícím obrázku: 
  
 ![Diagram zobrazující stránku můžete přejít na více stránkách.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Tato struktura se označuje jako pevná hierarchická topologie a pořadí, ve kterém je procházet hierarchii často stanovena v době běhu aplikace nebo uživatele. V době běhu každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více stránek shromažďuje data potřebná k určení stránku, která má přejít na. Následující obrázek znázorňuje jeden z několika možných navigace pořadí založen na předchozím obrázku:  
  
 ![Diagram zobrazující průběh pořadí navigace je to možné.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Přestože pořadí, ve kterém jsou stránky ve struktuře pevná hierarchická přejde je stanovena v době běhu, činnost koncového uživatele je stejné jako uživatelské prostředí u pevná lineární topologie:  
  
- Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce. Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.  
  
- Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).  
  
- Uživatelé můžou přecházet mezi stránky s využitím deníku.  
  
- Uživatelé mohou změnit pořadí navigace, pokud uživatel přejde zpět prostřednictvím deníku.  
  
- Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.  
  
- Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
- Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
- Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku. Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigace v dynamicky generovaném topologie  
 V některých aplikacích pořadí, ve kterém se přejde poté, dvě nebo více stránek lze pouze určit v době běhu podle uživatele, aplikace nebo externí data. Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvenci:  
  
 ![Sady stránek s neurčenou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Následující obrázek znázorňuje navigační sekvenci, který byl vybrán uživatelem v době běhu:  
  
 ![Diagram zobrazující průběh pořadí navigace zvolená v době běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Navigační sekvenci se označuje jako dynamicky generovaných topologií. Pro uživatele, stejně jako u jiných topologie navigace, činnost koncového uživatele je stejné je pro předchozí topologie:  
  
- Navigace na stránce volání Spouštěč stránku, která inicializuje průvodce a přejde na první stránce průvodce. Spouštěč stránky ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]– méně <xref:System.Windows.Navigation.PageFunction%601>) není vyžadováno, protože volání stránky můžete volat přímo na první stránku průvodce. Pomocí stránky Spouštěče, ale může zjednodušit inicializace průvodce, zejména v případě, že inicializace je složitá.  
  
- Uživatelé můžou přecházet mezi stránkami pomocí zpět a vpřed tlačítka (nebo hypertextové odkazy).  
  
- Uživatelé můžou přecházet mezi stránky s využitím deníku.  
  
- Uživatele můžete zrušit Průvodce na kterékoli stránce průvodce stisknutím tlačítka Storno.  
  
- Uživatelé můžou přijmout Průvodce na poslední stránce průvodce klepnutím na tlačítko Dokončit.  
  
- Pokud dojde ke zrušení průvodce, Průvodce vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Když uživatel přijme podmínky průvodce, Průvodce vrátí odpovídající výsledek a vrátí data, která se shromažďují.  
  
- Dokončení průvodce (přijata nebo bylo zrušeno), stránek, které se skládá z Průvodce se odeberou z deníku. Každá instance průvodce izolované, aby se předešlo potenciální dat nebo stavu anomálie se takto zachová.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Přehled strukturované navigace](structured-navigation-overview.md)
