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
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174196"
---
# <a name="navigation-topologies-overview"></a>Přehled topologií navigace
<a name="introduction"></a>Tento přehled poskytuje úvod do topologie navigace v WPF. Následně jsou diskutovány tři běžné navigační topologie se vzorky.  
  
> [!NOTE]
> Před přečtením tohoto tématu byste měli být obeznámeni s konceptem strukturované navigace v WPF pomocí funkcí stránky. Další informace o obou těchto tématech naleznete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).  
  
 Toto téma obsahuje následující oddíly:  
  
- [Navigační topologie](#Navigation_Topologies)  
  
- [Strukturované navigační topologie](#Structured_Navigation_Topologies)  
  
- [Navigace přes pevnou lineární topologii](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Dynamická navigace přes pevnou hierarchickou topologii](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Navigace přes dynamicky generovanou topologii](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a>Navigační topologie  
 Ve WPF se navigace obvykle skládá<xref:System.Windows.Controls.Page>ze stránek<xref:System.Windows.Documents.Hyperlink>( ) s hypertextovými odkazy ( ), které po klepnutí přecházejí na jiné stránky. Stránky, na které se naviguje, jsou označeny identifikátory prostředků (URI) (viz [Balení identifikátorů URI v wpf).](pack-uris-in-wpf.md) Vezměte v úvahu následující jednoduchý příklad, který zobrazuje stránky, hypertextové odkazy a jednotné identifikátory prostředků (URI):  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Tyto stránky jsou uspořádány v *navigační topologii,* jejíž struktura je určena tím, jak můžete procházet mezi stránkami. Tato konkrétní navigační topologie je vhodná v jednoduchých scénářích, i když navigace může vyžadovat složitější topologie, z nichž některé lze definovat pouze v případě, že je spuštěna aplikace.  
  
 Toto téma popisuje tři běžné navigační topologie: *pevné lineární*, *pevné hierarchické*a *dynamicky generované*. Každá navigační topologie je demonstrována [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se vzorkem, který má podobný ten, který je znázorněn na následujícím obrázku:  
  
 ![Stránky úkolů s datovými položkami a navigačními tlačítky.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a>Strukturované navigační topologie  
 Existují dva široké typy navigačních topologie:  
  
- **Pevná topologie**: definována v době kompilace a nemění se za běhu. Pevné topologie jsou užitečné pro navigaci přes pevnou sekvenci stránek v lineárním nebo hierarchickém pořadí.  
  
- **Dynamická topologie**: definována za běhu na základě vstupu, který je shromážděn od uživatele, aplikace nebo systému. Dynamické topologie jsou užitečné, když stránky lze procházet v různých sekvencích.  
  
 I když je možné vytvořit navigační topologie pomocí stránek, ukázky používají funkce stránky, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vracení dat prostřednictvím stránek topologie.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigace přes pevnou lineární topologii  
 Pevná lineární topologie je obdobou struktury průvodce, který má jednu nebo více stránek průvodce, které jsou navigovány v pevném pořadí. Následující obrázek znázorňuje strukturu vysoké úrovně a tok průvodce s pevnou lineární topologii:  
  
 ![Diagram, který zobrazuje pevnou lineární topologii.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Typické chování pro navigaci přes pevnou lineární topologii patří následující:  
  
- Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce. Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.  
  
- Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.  
  
- Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.  
  
- Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku. To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamická navigace přes pevnou hierarchickou topologii  
 V některých aplikacích stránky umožňují navigaci na dvě nebo více dalších stránek, jak je znázorněno na následujícím obrázku:
  
 ![Diagram, který zobrazuje stránku, která může přejít na více stránek.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Tato struktura se označuje jako pevná hierarchická topologie a pořadí, ve kterém je hierarchie provázána, je často určeno za běhu aplikací nebo uživatelem. Za běhu každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více dalších stránek, shromažďuje data potřebná k určení stránky, na kterou chcete přejít. Následující obrázek znázorňuje jednu z několika možných navigačních sekvencí na základě předchozího obrázku:  
  
 ![Diagram, který ukazuje možnou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 I když pořadí, ve kterém jsou stránky v pevné hierarchické struktuře navigovány, je určeno za běhu, uživatelské prostředí je stejné jako uživatelské prostředí pro pevnou lineární topologii:  
  
- Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce. Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.  
  
- Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou změnit navigační pořadí, pokud projdou zpět deníkem.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.  
  
- Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.  
  
- Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku. To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigace přes dynamicky generovanou topologii  
 V některých aplikacích pořadí, ve kterém jsou procházeny dvě nebo více stránek lze určit pouze za běhu, ať už uživatelem, aplikace nebo externí data. Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvencí:  
  
 ![Sada stránek s neurčenou navigační sekvencí.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Následující obrázek znázorňuje navigační sekvenci, která byla vybrána uživatelem za běhu:  
  
 ![Diagram, který zobrazuje navigační sekvenci zvolenou za běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Navigační sekvence se označuje jako dynamicky generovaná topologie. Pro uživatele, stejně jako u ostatních topologie navigace, uživatelské prostředí je stejné jako pro předchozí topologie:  
  
- Přechod ze stránky volajícího na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)](a <xref:System.Windows.Navigation.PageFunction%601>-less) není vyžadována, protože volající stránka může volat přímo první stránku průvodce. Použití stránky spouštěče však může zjednodušit inicializaci průvodce, zejména pokud je inicializace složitá.  
  
- Uživatelé mohou přecházet mezi stránkami pomocí tlačítek Zpět a Vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka Storno.  
  
- Uživatelé mohou průvodce přijmout na poslední stránce průvodce stisknutím tlačítka Dokončit.  
  
- Pokud je průvodce zrušen, vrátí odpovídající výsledek a nevrátí žádná data.  
  
- Pokud uživatel přijme průvodce, vrátí odpovídající výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijato nebo zrušeno) budou stránky, které průvodce obsahuje, odebrány z deníku. To udržuje každou instanci průvodce izolované, čímž se zabrání potenciální data nebo státní anomálie.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Přehled strukturované navigace](structured-navigation-overview.md)
