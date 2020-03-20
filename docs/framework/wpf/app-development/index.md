---
title: Vývoj aplikací
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186006"
---
# <a name="application-development"></a>Vývoj aplikací
<a name="introduction"></a>Windows Presentation Foundation (WPF) je prezentační architektura, kterou lze použít k vývoji následujících typů aplikací:  
  
- Samostatné aplikace (tradiční styl aplikace systému Windows vytvořené jako spustitelná sestavení, která jsou nainstalována do klientského počítače a spouštěna z ní).  
  
- Aplikace prohlížeče XAML (XBAPs) (aplikace složené z navigačních stránek, které jsou vytvořeny jako spustitelná sestavení a hostované webovými prohlížeči, jako je Microsoft Internet Explorer nebo Mozilla Firefox).  
  
- Vlastní knihovny ovládacích prvků (nespustitelná sestavení obsahující opakovaně použitelné ovládací prvky).  
  
- Knihovny tříd (nespustitelná sestavení, která obsahují opakovaně použitelné třídy).  
  
> [!NOTE]
> Použití wpf typů ve službě systému Windows se důrazně nedoporučuje. Pokud se pokusíte použít tyto funkce ve službě systému Windows, nemusí fungovat podle očekávání.  
  
 Chcete-li vytvořit tuto sadu aplikací, WPF implementuje celou řadu služeb. Toto téma obsahuje přehled těchto služeb a kde najít další informace.  

<a name="Application_Management"></a>
## <a name="application-management"></a>Správa aplikací  
 Spustitelné aplikace WPF obvykle vyžadují základní sadu funkcí, která zahrnuje následující:  
  
- Vytváření a správa společné aplikační infrastruktury (včetně vytvoření metody vstupního bodu a smyčky zpráv systému Windows pro příjem systémových a vstupních zpráv).  
  
- Sledování a interakce s životností aplikace.  
  
- Načítání a zpracování parametrů příkazového řádku.  
  
- Sdílení vlastností a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prostředků oboru aplikace.  
  
- Zjišťování a zpracování neošetřených výjimek.  
  
- Vracím únikové kódy.  
  
- Správa oken v samostatných aplikacích.  
  
- Sledování navigace v aplikacích prohlížeče XAML (XBAPs) a samostatných aplikacích s navigačními okny a rámečky.  
  
 Tyto funkce jsou <xref:System.Windows.Application> implementovány třídou, kterou přidáte do aplikací pomocí *definice aplikace*.  
  
 Další informace naleznete v [tématu Application Management Overview](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF  
 WPF rozšiřuje základní podporu v rozhraní Microsoft .NET Framework pro vložené prostředky s podporou pro tři druhy nespustitelných datových souborů: prostředek, obsah a data. Další informace naleznete v [tématu WPF Aplikační zdroj, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).  
  
 Klíčovou součástí podpory nespustitelných datových souborů WPF je schopnost identifikovat a načíst je pomocí jedinečného identifikátoru URI. Další informace naleznete [v tématu Pack URI v WPF](pack-uris-in-wpf.md).  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>Okna a dialogová okna  
 Uživatelé interagují se samostatnými aplikacemi WPF prostřednictvím oken. Účelem okna je hostovat obsah aplikace a zpřístupnit funkce aplikace, které obvykle umožňují uživatelům pracovat s obsahem. V WPF jsou okna zapouzdřena třídou, <xref:System.Windows.Window> která podporuje:  
  
- Vytváření a zobrazování oken.  
  
- Vytvoření vztahů mezi vlastníkem/vlastněným oknem.  
  
- Konfigurace vzhledu okna (například velikost, umístění, ikony, text záhlaví, ohraničení).  
  
- Sledování a interakce s životností okna.  
  
 Další informace naleznete v tématu [WPF Windows Overview](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window>podporuje možnost vytvořit speciální typ okna známého jako dialogové okno. Lze vytvořit modální i nemodální typy dialogových oken.  
  
 Pro větší pohodlí a výhody opětovného použití a konzistentní uživatelské prostředí napříč aplikacemi wpf <xref:Microsoft.Win32.SaveFileDialog>zveřejňuje <xref:System.Windows.Controls.PrintDialog>tři běžná dialogová okna systému Windows: <xref:Microsoft.Win32.OpenFileDialog>, , a .  
  
 Okno se zprávou je speciální typ dialogového okna pro zobrazení důležitých textových informací uživatelům a pro kladení jednoduchých otázek Ano/Ne/OK/Zrušení. Třídu <xref:System.Windows.MessageBox> slouží k vytvoření a zobrazení oken zpráv.  
  
 Další informace naleznete v [tématu Přehled dialogových oken](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navigace  
 WPF podporuje webovou navigaci<xref:System.Windows.Controls.Page>pomocí stránek (<xref:System.Windows.Documents.Hyperlink>) a hypertextových odkazů ( ). Navigace může být implementována různými způsoby, které zahrnují následující:  
  
- Samostatné stránky, které jsou hostovány ve webovém prohlížeči.  
  
- Stránky zkompilované do XBAP, který je hostován ve webovém prohlížeči.  
  
- Stránky zkompilované do samostatné aplikace a hostované navigačním oknem (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Stránky, které jsou hostovány<xref:System.Windows.Controls.Frame>rámcem ( ), které mohou být hostovány na samostatné stránce, nebo stránky zkompilované do XBAP nebo samostatné aplikace.  
  
 Pro usnadnění navigace wpf implementuje následující:  
  
- <xref:System.Windows.Navigation.NavigationService>, sdílený navigační modul pro zpracování navigačních <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>požadavků používaných aplikacemi , a XBAPs pro podporu navigace v rámci aplikace.  
  
- Navigační metody pro zahájení navigace.  
  
- Navigační události pro sledování a interakci s životností navigace.  
  
- Zapamatování zpět a vpřed navigace pomocí deníku, který může být také kontrolována a manipulovat.  
  
 Další informace naleznete v [tématu Navigační přehled](navigation-overview.md).  
  
 WPF také podporuje speciální typ navigace známý jako strukturované navigace. Strukturované navigace lze volat jednu nebo více stránek, které vracejí data strukturovaným a předvídatelným způsobem, který je konzistentní s volající funkce. Tato funkce závisí <xref:System.Windows.Navigation.PageFunction%601> na třídě, která je popsána dále ve [strukturované navigační přehled](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601>slouží také ke zjednodušení vytváření složitých navigačních topologie, které jsou popsány v [přehledu navigačních topologií](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>
## <a name="hosting"></a>Hostování  
 XBAPs mohou být hostovány v aplikaci Microsoft Internet Explorer nebo Firefox. Každý hostingový model má svou vlastní sadu úvah a omezení, které jsou zahrnuty v [Hostingu](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>Sestavení a nasazení  
 Přestože jednoduché wpf aplikace lze sestavit z příkazového řádku pomocí kompilátorů příkazového řádku, WPF integruje s Visual Studio poskytovat další podporu, která zjednodušuje vývoj a proces sestavení. Další informace naleznete [v tématu Vytváření aplikace WPF](building-a-wpf-application-wpf.md).  
  
 V závislosti na typu aplikace, kterou vytvoříte, existuje jedna nebo více možností nasazení, ze kterých si můžete vybrat. Další informace naleznete [v tématu Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Přehled správy aplikací](application-management-overview.md)|Obsahuje přehled třídy včetně správy životnosti <xref:System.Windows.Application> aplikace, oken, prostředků aplikace a navigace.|  
|[Okna ve WPF](windows-in-wpf-applications.md)|Obsahuje podrobnosti o správě oken v <xref:System.Windows.Window> aplikaci, včetně použití třídy a dialogových oken.|  
|[Přehled navigace](navigation-overview.md)|Obsahuje přehled správy navigace mezi stránkami aplikace.|  
|[Hostování](hosting-wpf-applications.md)|Obsahuje přehled aplikací prohlížeče XAML (XBAPs).|  
|[Sestavení a nasazení](building-and-deploying-wpf-applications.md)|Popisuje, jak vytvořit a nasadit aplikaci WPF.|  
|[Úvod k použití WPF v sadě Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Popisuje hlavní rysy WPF.|  
|[Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Návod, který ukazuje, jak vytvořit aplikaci WPF pomocí navigace na stránce, rozložení, ovládací prvky, obrázky, styly a vazby.|
