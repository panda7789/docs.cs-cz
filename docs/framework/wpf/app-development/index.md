---
title: Vývoj aplikací
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 3b7e1d04173741088935104e8d4225691927a27b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211059"
---
# <a name="application-development"></a>Vývoj aplikací
<a name="introduction"></a> Windows Presentation Foundation (WPF) je prezentační architektura, která slouží k vytvoření následujících typů aplikací:  
  
-   Samostatné aplikace (tradiční styl [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikace vytvořené jako spustitelný soubor sestavení, které jsou nainstalovány na a spustit z klientského počítače).  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] (aplikace složené z navigace stránky, které jsou vytvořené jako spustitelný soubor sestavení a hostitelem webových prohlížečů jako [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] nebo Mozilla Firefox).  
  
-   Vlastní ovládací prvek knihovny (-spustitelný soubor sestavení, která obsahují opakovaně použitelné ovládací prvky).  
  
-   Knihovny tříd (-spustitelný soubor sestavení, které obsahují opakovaně použitelné třídy).  
  
> [!NOTE]
>  Použití typů WPF ve službě Windows se důrazně nedoporučuje. Při pokusu o použití těchto funkcí ve službě Windows, nemusí fungovat podle očekávání.  
  
 K vytvoření této sady aplikací, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje celou řadu služeb. Toto téma obsahuje přehled těchto služeb a kde najít další informace.  

<a name="Application_Management"></a>   
## <a name="application-management"></a>Správa aplikací  
 Spustitelný soubor [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace obvykle vyžadují základní sadu funkcí, které zahrnují následující:  
  
-   Vytváření a správa infrastruktury běžné aplikace (včetně vytvoření metodu vstupního bodu a smyčku zpráv Windows na systém a zprávy o zadávání).  
  
-   Sledování a interakci s životního cyklu aplikace.  
  
-   Načítání a zpracování parametrů příkazového řádku.  
  
-   Sdílení vlastností pro rozsah aplikace a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prostředky.  
  
-   Zjištění a zpracování neošetřených výjimek.  
  
-   Vrátí ukončovací kód.  
  
-   Správa systému windows v samostatné aplikace.  
  
-   Sledování navigace v [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]a samostatné aplikace s windows navigace a snímků.  
  
 Tyto funkce jsou implementované <xref:System.Windows.Application> třídy, které přidáte do vaší aplikace s použitím *definice aplikace*.  
  
 Další informace najdete v tématu [přehled správy aplikací](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozšiřuje podporu core v rozhraní Microsoft .NET Framework pro vložené prostředky díky podpoře pro tři druhy – spustitelný soubor datové soubory: zdroj, obsah a data. Další informace najdete v tématu [prostředek aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).  
  
 Klíčovou součástí podporu pro WPF – spustitelný soubor datových souborů je schopnost identifikovat a načíst pomocí jedinečný [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]. Další informace najdete v tématu [identifikátory Pack URI v subsystému WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Windows a dialogových oknech  
 Uživatelé komunikují s [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] samostatné aplikace pomocí systému windows. Účelem okna je hostovat obsah aplikace a vystavit funkčnost aplikace obvykle umožňuje uživatelům pracovat s obsahem. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], systému windows jsou zapouzdřena objektem <xref:System.Windows.Window> třídy, která podporuje:  
  
-   Vytváření a zobrazení windows.  
  
-   Umožňují vytvářet vlastníka/vlastní relace okna.  
  
-   Konfigurace vzhledu okno (například velikost, umístění, ikony, text záhlaví, ohraničení).  
  
-   Sledování a interakci s životnost časového období.  
  
 Další informace najdete v tématu [přehled WPF Windows](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> podporuje schopnost vytvářet speciální typ známé jako dialogové okno. Modální a nemodální dialogová okna typy je možné vytvořit.  
  
 Pro usnadnění práce a výhody pro opětovné použití a konzistentní uživatelské prostředí napříč aplikacemi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje tři společná dialogová okna Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>, a <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno se zprávou je zvláštní druh dialogové okno pro zobrazení důležité textové informace pro uživatele a pro kladení otázek jednoduché Ano/Ne/OK nebo zrušit. Můžete použít <xref:System.Windows.MessageBox> třídy k vytvoření a zobrazení okna se zprávou.  
  
 Další informace najdete v tématu [přehled dialogových oken](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje navigaci webových stránkách (<xref:System.Windows.Controls.Page>) a hypertextových odkazů (<xref:System.Windows.Documents.Hyperlink>). Navigace je implementovat v mnoha různými způsoby, které zahrnují následující:  
  
-   Samostatné stránky, které jsou hostované ve webovém prohlížeči.  
  
-   Stránky kompilovány do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , která je hostována ve webovém prohlížeči.  
  
-   Stránky kompilovány do samostatné aplikace a hostitelem navigačním okně (<xref:System.Windows.Navigation.NavigationWindow>).  
  
-   Stránky, které jsou hostovány blok (<xref:System.Windows.Controls.Frame>), které mohly být hostovány na samostatné stránce nebo stránky kompilovány do buď [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] nebo samostatné aplikace.  
  
 Pro usnadnění navigace, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implementuje následující:  
  
-   <xref:System.Windows.Navigation.NavigationService>, sdílené navigační modul pro zpracování žádosti o navigaci pomocí, který používá <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>, a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] pro podporu uvnitř aplikační navigace.  
  
-   Navigační metody k zahájení navigace.  
  
-   Navigační události ke sledování a interakci s dobou života navigace.  
  
-   Zapamatování zpět a vpřed vymazávat pomocí deníku, které lze také prozkoumat a manipulovat.  
  
 Informace najdete v tématu [Přehled navigace](navigation-overview.md).  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporuje také speciální typ navigace označované jako strukturované navigace. Strukturované navigace umožňuje volat jednu nebo více stránek, které nevracejí data, která je kompatibilní s voláním funkce způsobem strukturovaných a předvídatelné. Tato schopnost závisí <xref:System.Windows.Navigation.PageFunction%601> třídu, která je popsána dále v [přehled strukturované navigace](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> slouží také k zjednodušení vytváření složitých navigace topologií, které jsou popsány v [přehled topologií navigace](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hostování  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] je možné hostovat v [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] nebo Firefox. Každý model hostingu má svou vlastní sadu aspektů a omezení, která se věnuje [Hosting](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Sestavení a nasazení  
 I když je jednoduchý [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace se dají vytvářet z příkazového řádku použití kompilátorů příkazového řádku, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] integruje [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] poskytovat další podporu, která zjednodušený proces vývoje a sestavení. Další informace najdete v tématu [sestavení aplikace WPF](building-a-wpf-application-wpf.md).  
  
 V závislosti na typu aplikace, které vytváříte jsou jedna nebo více možností nasazení lze vybírat. Další informace najdete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled správy aplikací](application-management-overview.md)|Najdete zde přehled <xref:System.Windows.Application> třídy, včetně správy životního cyklu aplikací, windows, prostředků aplikace a navigace.|  
|[Windows ve WPF](windows-in-wpf-applications.md)|Poskytuje podrobné informace o správě windows ve vaší aplikaci, včetně použití <xref:System.Windows.Window> třídy a v dialogových oknech.|  
|[Přehled navigace](navigation-overview.md)|Poskytuje přehled správy navigace mezi stránkami vaší aplikace.|  
|[Hostování](hosting-wpf-applications.md)|Poskytuje přehled o [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].|  
|[Sestavení a nasazení](building-and-deploying-wpf-applications.md)|Popisuje, jak sestavit a nasadit aplikaci WPF.|  
|[Úvod k použití WPF v sadě Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Popisuje hlavní funkce WPF.|  
|[Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Návod, který ukazuje, jak vytvořit WPF aplikace s využitím stránce navigace, rozložení, ovládací prvky, obrázků, styly a vazby.|
