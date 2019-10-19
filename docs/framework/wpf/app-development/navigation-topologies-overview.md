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
ms.openlocfilehash: 5d9b09085ed8057f53cae9f9177682b01e698f6d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580712"
---
# <a name="navigation-topologies-overview"></a>Přehled topologií navigace
<a name="introduction"></a>Tento přehled poskytuje Úvod k topologiím navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Následně jsou popsány tři běžné topologie navigace s ukázkami.  
  
> [!NOTE]
> Před čtením tohoto tématu byste měli být obeznámeni s konceptem strukturované navigace v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pomocí funkcí stránky. Další informace o obou těchto tématech najdete v tématu [Přehled strukturované navigace](structured-navigation-overview.md).  
  
 Toto téma obsahuje následující oddíly:  
  
- [Topologie navigace](#Navigation_Topologies)  
  
- [Strukturované navigační topologie](#Structured_Navigation_Topologies)  
  
- [Navigace přes pevnou lineární topologii](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Dynamická navigace nad pevnou hierarchickou topologií](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Navigace prostřednictvím dynamicky generované topologie](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie navigace  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se navigace obvykle skládá ze stránek (<xref:System.Windows.Controls.Page>) s hypertextovými odkazy (<xref:System.Windows.Documents.Hyperlink>), které po kliknutí přejdou na jiné stránky. Stránky, na které se navigují, se identifikují pomocí identifikátorů URI (Uniform Resource Identifier) (viz [identifikátory URI balíčku v WPF](pack-uris-in-wpf.md)). Vezměte v úvahu následující jednoduchý příklad, který ukazuje stránky, hypertextové odkazy a identifikátory URI (Uniform Resource Identifier):  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Tyto stránky jsou uspořádány do *navigační topologie* , jejíž struktura je určena podle toho, jak můžete mezi stránkami přecházet. Tato konkrétní navigační topologie je vhodná v jednoduchých scénářích, i když navigace může vyžadovat složitější topologie, některé z nich lze definovat pouze v případě, že je aplikace spuštěna.  
  
 V tomto tématu se dozvíte o třech běžných topologiích navigace: *pevné lineární*, *pevné hierarchické*a *dynamicky generované*. Každá navigační topologie je znázorněna s ukázkou, která má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jako na následujícím obrázku:  
  
 ![Stránky úloh s datovými položkami a navigačními tlačítky.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Strukturované navigační topologie  
 Existují dva široké typy topologií navigace:  
  
- **Pevná topologie**: definována v době kompilace a v době běhu se nemění. Pevné topologie jsou užitečné pro navigaci prostřednictvím pevné sekvence stránek lineárním nebo hierarchickém řazením.  
  
- **Dynamická topologie**: definuje se v době běhu na základě vstupu, který se shromažďuje od uživatele, aplikace nebo systému. Dynamické topologie jsou užitečné, když lze stránky procházet v různých sekvencích.  
  
 I když je možné vytvořit navigační topologie pomocí stránek, ukázky používají funkce stránky, protože poskytují další podporu, která zjednodušuje podporu pro předávání a vracení dat prostřednictvím stránek topologie.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navigace přes pevnou lineární topologii  
 Pevná lineární topologie je podobná struktuře průvodce, který obsahuje jednu nebo více stránek průvodce, které jsou v pevné sekvenci. Následující obrázek ukazuje strukturu vysoké úrovně a tok průvodce s pevnou lineární topologií:  
  
 ![Diagram, který zobrazuje pevnou lineární topologii.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Typické chování pro navigaci přes pevnou lineární topologii zahrnuje následující:  
  
- Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo. Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.  
  
- Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.  
  
- Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.  
  
- Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.  
  
- Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje. Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamická navigace nad pevnou hierarchickou topologií  
 V některých aplikacích stránky umožňují navigaci na dvě nebo více dalších stránek, jak je znázorněno na následujícím obrázku: 
  
 ![Diagram, který zobrazuje stránku, která může přejít na více stránek.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Tato struktura je známá jako pevná hierarchická topologie a pořadí, ve kterém je hierarchie procházena, je často určeno v době spuštění aplikací nebo uživatelem. V době spuštění každá stránka v hierarchii, která umožňuje navigaci na dvě nebo více dalších stránek, shromažďuje data potřebná k určení stránky, na kterou se má přejít. Následující obrázek znázorňuje jednu z několika možných navigačních sekvencí v závislosti na předchozím obrázku:  
  
 ![Diagram, který zobrazuje možnou navigační sekvenci.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 I když je pořadí, ve kterém se stránky v pevné hierarchické struktuře procházejí, určuje za běhu, činnost koncového uživatele je stejná jako činnost koncového uživatele pro pevnou lineární topologii:  
  
- Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo. Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.  
  
- Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou navigační sekvenci změnit, pokud procházejí zpět prostřednictvím deníku.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.  
  
- Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.  
  
- Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.  
  
- Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje. Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navigace prostřednictvím dynamicky generované topologie  
 V některých aplikacích je pořadí, ve kterém se dvě nebo více stránek prochází, dá určit jenom za běhu, ať už podle uživatele, aplikace nebo externích dat. Následující obrázek znázorňuje sadu stránek s neurčenou navigační sekvencí:  
  
 ![Sada stránek s neurčenou navigační sekvencí.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Následující obrázek znázorňuje navigační sekvenci, kterou uživatel zvolil v době běhu:  
  
 ![Diagram, který zobrazuje navigační sekvenci zvolenou v době běhu.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Navigační sekvence je označována jako dynamicky generovaná topologie. Pro uživatele stejně jako u ostatních topologií navigace je prostředí uživatele stejné jako u předchozích topologií:  
  
- Přechod z volající stránky na stránku spouštěče, která inicializuje průvodce a přejde na první stránku průvodce. Stránka spouštěče ([!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bez <xref:System.Windows.Navigation.PageFunction%601>) není vyžadována, protože volající stránka může zavolat první stránku průvodce přímo. Použití stránky spouštěče může ale zjednodušit inicializaci průvodce, zejména v případě, že je inicializace složitá.  
  
- Uživatelé mohou procházet mezi stránkami pomocí tlačítek zpět a vpřed (nebo hypertextových odkazů).  
  
- Uživatelé mohou procházet mezi stránkami pomocí deníku.  
  
- Uživatelé mohou zrušit průvodce z libovolné stránky průvodce stisknutím tlačítka zrušit.  
  
- Kliknutím na tlačítko Dokončit můžete uživatelům přijmout Průvodce na poslední stránce průvodce.  
  
- Pokud se Průvodce zruší, průvodce vrátí příslušný výsledek a nevrátí žádná data.  
  
- Pokud uživatel Průvodce přijme, průvodce vrátí příslušný výsledek a vrátí shromážděná data.  
  
- Po dokončení průvodce (přijatý nebo zrušený) se z deníku odeberou stránky, které průvodce obsahuje. Tím se udržuje všechny instance průvodce izolované, takže se vyhnete potenciálním anomáliím dat nebo stavu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Přehled strukturované navigace](structured-navigation-overview.md)
