---
title: "Vývoj aplikací"
ms.custom: 
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d2a79a05f18fecf4e008aa6a95d359c719e854b
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="application-development"></a>Vývoj aplikací
<a name="introduction"></a>
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]je rozhraní prezentace, které slouží k vytvoření následujících typů aplikací:  
  
-   Samostatné aplikace (tradiční styl [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikace vytvořené jako spustitelný soubor sestavení, které jsou nainstalovány na a spustit z klientského počítače).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)](aplikace skládá z navigace stránky, které jsou vytvořené jako spustitelný soubor sestavení a hostované ve webových prohlížečů, jako je například [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] nebo Mozilla Firefox).  
  
-   Vlastní ovládací prvek knihovny (obsahující opakovaně použitelných ovládacích prvků-spustitelný soubor sestavení).  
  
-   Knihovny tříd (-spustitelný soubor sestavení, které obsahují opakovaně použitelné třídy).  
  
> [!NOTE]
>  Použití typů WPF ve službě Windows není doporučeno. Pokud se pokusíte použít tyto funkce ve službě Windows, nemusí fungovat podle očekávání.  
  
 K vytvoření této sadu aplikací, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje hostitele služby. Toto téma obsahuje přehled těchto služeb a kde najít další informace.  
  

  
<a name="Application_Management"></a>   
## <a name="application-management"></a>Správa aplikací  
 Spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace běžně vyžadují základní sady funkcí, které zahrnují následující:  
  
-   Vytváření a správa běžnou infrastrukturu aplikace (včetně vytváření metodu vstupní bod a smyčku zpráv systému Windows pro příjem systému a vstupní zprávy).  
  
-   Sledování a interakci s životního cyklu aplikace.  
  
-   Načítání a zpracování parametry příkazového řádku.  
  
-   Vlastnosti oboru aplikace pro sdílení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prostředky.  
  
-   Zjišťování a zpracování neošetřených výjimek.  
  
-   Vrátí ukončovací kód.  
  
-   Správa systému windows v samostatné aplikace.  
  
-   Sledování navigace ve [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]a samostatné aplikace s navigační windows a rámce.  
  
 Tyto možnosti jsou implementované <xref:System.Windows.Application> třídy, která přidáte do vaší aplikace s použitím *definice aplikace*.  
  
 Další informace najdete v tématu [přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]rozšiřuje podporu jádra v [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] pro vložené prostředky s podporou pro tři druhy-spustitelný soubor datových souborů: prostředků, obsah a data. Další informace najdete v tématu [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Klíčovou součástí podporu WPF-spustitelný soubor datových souborů je umožňují identifikovat a načíst pomocí jedinečný [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Další informace najdete v tématu [Pack identifikátory URI v grafickém subsystému WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Systém Windows a dialogových oken  
 Uživatelé komunikovat s [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace prostřednictvím služby windows. Účelem časového období je obsah, aplikace a funkcionalitu aplikace, která obvykle umožňuje uživatelům interakci s obsahem. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], windows se zapouzdřené pomocí <xref:System.Windows.Window> třídy, který podporuje:  
  
-   Vytváření a zobrazující systému windows.  
  
-   Vytvoření vztahů okno vlastníka nebo ve vlastnictví.  
  
-   Konfigurace vzhledu okno (například velikost, umístění, ikony, text záhlaví, ohraničení).  
  
-   Sledování a interakci s životnost časového období.  
  
 Další informace najdete v tématu [WPF ve Windows – přehled](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>podporuje možnost vytvořit zvláštní typ známé jako dialogové okno. Modální a nemodální dialogová okna typy lze vytvořit.  
  
 Pro usnadnění práce a výhody – opětovné použití a konzistentní podmínky koncového uživatele ve všech aplikacích [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpřístupní tři nejběžnější [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] dialogových oken: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, a <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno se zprávou je zvláštní druh dialogové okno pro zobrazení důležité textové informace pro uživatele a klást otázky jednoduché Ano/Ne/OK nebo zrušit. Můžete použít <xref:System.Windows.MessageBox> třída k vytvoření a zobrazení oken zpráv.  
  
 Další informace najdete v tématu [dialogové okno Přehled polí](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]podporuje stylu webové navigace pomocí stránek (<xref:System.Windows.Controls.Page>) a hypertextové odkazy (<xref:System.Windows.Documents.Hyperlink>). Navigace, můžou se implementovat v mnoha různými způsoby, které zahrnují následující:  
  
-   Samostatné stránky, které jsou hostované ve webovém prohlížeči.  
  
-   Stránky kompilovány do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hostující ve webovém prohlížeči.  
  
-   Stránky kompilovány do samostatné aplikace a hostované navigačním okně (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Stránky, které jsou hostované rámeček (<xref:System.Windows.Controls.Frame>), který může být hostovaný na samostatné stránce nebo na stránce zkompilovat do buď [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] nebo samostatné aplikace.  
  
 Pro usnadnění navigace, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje následující:  
  
-   <xref:System.Windows.Navigation.NavigationService>, modul sdílené navigace pro zpracování požadavků navigace, který používá <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pro podporu navigační uvnitř aplikace.  
  
-   Navigační metody zahájíte navigace.  
  
-   Navigace události ke sledování a interakci s navigační životnosti.  
  
-   Zapamatování zpět a předat dál navigace pomocí deníku, které můžete také být prověřovány a s nimi manipulovat.  
  
 Informace najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]podporuje také zvláštním typem navigace známé jako strukturovaný navigace. Strukturované navigační slouží k volání jednu nebo více stránek, které vrátit data strukturovaných a předvídatelné tak, že je v souladu s volání funkcí. Tato funkce závisí na <xref:System.Windows.Navigation.PageFunction%601> třída, která je popsány dále v [strukturovaných navigační přehled](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601>slouží také k zjednodušení vytváření složitých navigační topologie, které jsou popsány v [přehled topologie navigační](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hostování  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]je možné hostovat v [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] nebo Firefox. Každý hostitelský model má vlastní sadu požadavky a omezení, které jsou popsané v [hostitelský](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Sestavení a nasazení  
 I když je jednoduchý [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace se dají vytvářet z příkazového řádku pomocí kompilátory příkazového řádku, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se integruje s [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] poskytovat další podporu, který zjednodušený proces vývoje a sestavení. Další informace najdete v tématu [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
 V závislosti na typu aplikace, kterou vytvoříte se jedna nebo více možností nasazení lze vybírat. Další informace najdete v tématu [nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled správy aplikací](../../../../docs/framework/wpf/app-development/application-management-overview.md)|Obsahuje přehled <xref:System.Windows.Application> třídy, včetně správy životního cyklu aplikací, windows, prostředky aplikace a navigace.|  
|[Windows ve WPF](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|Poskytuje podrobné informace o správě systému windows ve vaší aplikaci, včetně toho, jak používat <xref:System.Windows.Window> třídy a dialogové okno polí.|  
|[Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md)|Poskytuje přehled správy navigace mezi stránkami vaší aplikace.|  
|[Hostování](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|Obsahuje přehled [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Sestavení a nasazení](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|Popisuje, jak vytvářet a nasazovat aplikace WPF.|  
|[Úvod k použití WPF v sadě Visual Studio](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|Popisuje hlavní funkce WPF.|  
|[Návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|Návod, který ukazuje, jak vytvořit WPF aplikace pomocí stránky navigace, rozložení, ovládací prvky, Image, styly a vazbu.|
