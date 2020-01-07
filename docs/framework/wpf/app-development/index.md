---
title: Vývoj aplikací
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: b0bdf49e0bb3d9bfa3fc4e7fd94aa68ee4ea0bb3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636390"
---
# <a name="application-development"></a>Vývoj aplikací
<a name="introduction"></a>Windows Presentation Foundation (WPF) je prezentační rozhraní, které lze použít k vývoji následujících typů aplikací:  
  
- Samostatné aplikace (tradiční styly aplikací pro Windows postavené jako spustitelná sestavení, která jsou nainstalovaná a spouštěná z klientského počítače).  
  
- Aplikace prohlížeče XAML (XBAP) (aplikace tvořené navigačními stránkami, které jsou sestaveny jako spustitelná sestavení a hostovány webovými prohlížeči, jako je například Microsoft Internet Explorer nebo Mozilla Firefox).  
  
- Vlastní knihovny ovládacích prvků (nespustitelná sestavení obsahující opakovaně použitelné ovládací prvky).  
  
- Knihovny tříd (nespustitelná sestavení, která obsahují opakovaně použitelné třídy).  
  
> [!NOTE]
> Použití typů WPF ve službě systému Windows se důrazně nedoporučuje. Pokud se pokusíte tyto funkce použít ve službě systému Windows, nemusí fungovat podle očekávání.  
  
 Pro sestavení této sady aplikací WPF implementuje hostitele služeb. V tomto tématu najdete přehled těchto služeb a kde najdete další informace.  

<a name="Application_Management"></a>   
## <a name="application-management"></a>Správa aplikací  
 Spustitelné aplikace WPF běžně vyžadují základní sadu funkcí, které zahrnují následující:  
  
- Vytvoření a Správa běžné aplikační infrastruktury (včetně vytvoření metody vstupního bodu a smyčky zpráv systému Windows pro příjem systémových a vstupních zpráv).  
  
- Sledování a interakce s životností aplikace.  
  
- Načítání a zpracování parametrů příkazového řádku.  
  
- Sdílení vlastností oboru aplikace a prostředků [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
- Zjišťování a zpracování neošetřených výjimek.  
  
- Vracení ukončovacích kódů  
  
- Správa systému Windows v samostatných aplikacích.  
  
- Sledování navigace v aplikacích prohlížeče XAML (XBAP) a samostatné aplikace s navigačními okny a snímky.  
  
 Tyto možnosti jsou implementovány třídou <xref:System.Windows.Application>, kterou přidáte do aplikací pomocí *definice aplikace*.  
  
 Další informace najdete v tématu [Přehled správy aplikací](application-management-overview.md).  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## <a name="wpf-application-resource-content-and-data-files"></a>Zdroj, obsah a datové soubory zdroje aplikací WPF  
 WPF rozšiřuje základní podporu v Microsoft .NET Framework pro vložené prostředky a podporuje tři druhy nespustitelných datových souborů: zdroj, obsah a data. Další informace naleznete v tématu [prostředky aplikace WPF, obsah a datové soubory](wpf-application-resource-content-and-data-files.md).  
  
 Klíčovou součástí podpory pro nespustitelné datové soubory WPF je schopnost identifikovat a načíst je pomocí jedinečného identifikátoru URI. Další informace najdete v tématu [identifikátory URI Pack v](pack-uris-in-wpf.md)subsystému WPF.  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## <a name="windows-and-dialog-boxes"></a>Okna a dialogová okna  
 Uživatelé pracují se samostatnými aplikacemi WPF prostřednictvím systému Windows. Účelem okna je hostování obsahu aplikace a vystavení funkcí aplikace, které obvykle uživatelům umožňují pracovat s obsahem. V WPF je Windows zapouzdřený pomocí <xref:System.Windows.Window> třídy, která podporuje:  
  
- Vytváření a zobrazování oken.  
  
- Vytváření vztahů mezi vlastníkem a vlastníkem okna.  
  
- Konfigurace vzhledu okna (například velikost, umístění, ikony, text záhlaví, ohraničení).  
  
- Sledování a interakce s dobou života okna.  
  
 Další informace najdete v tématu [Přehled Windows WPF](wpf-windows-overview.md).  
  
 <xref:System.Windows.Window> podporuje možnost vytvoření speciálního typu okna označovaného jako dialogové okno. Lze vytvořit modální i nemodální typy dialogových oken.  
  
 Pro usnadnění a výhody opětovné použitelnosti a konzistentní uživatelské prostředí napříč aplikacemi poskytuje WPF tři z dialogových oken běžné Windows: <xref:Microsoft.Win32.OpenFileDialog>, <xref:Microsoft.Win32.SaveFileDialog>a <xref:System.Windows.Controls.PrintDialog>.  
  
 Okno se zprávou je speciální typ dialogového okna pro zobrazení důležitých textových informací uživatelům a pro dotazování jednoduchých dotazů Ano/Ne/OK/zrušit. Pro vytváření a zobrazování oken se zprávami se používá třída <xref:System.Windows.MessageBox>.  
  
 Další informace najdete v tématu [Přehled dialogových oken](dialog-boxes-overview.md).  
  
<a name="Navigation"></a>   
## <a name="navigation"></a>Navigace  
 WPF podporuje navigaci na webovém stylu pomocí stránek (<xref:System.Windows.Controls.Page>) a hypertextových odkazů (<xref:System.Windows.Documents.Hyperlink>). Navigace může být implementována různými způsoby, které zahrnují následující:  
  
- Samostatné stránky, které jsou hostovány ve webovém prohlížeči.  
  
- Stránky zkompilované do XBAP, která je hostována ve webovém prohlížeči.  
  
- Stránky zkompilované do samostatné aplikace a hostované v navigačním okně (<xref:System.Windows.Navigation.NavigationWindow>).  
  
- Stránky hostované snímkem (<xref:System.Windows.Controls.Frame>), které mohou být hostovány na samostatné stránce nebo na stránce zkompilované do aplikace XBAP nebo samostatné aplikace.  
  
 Pro usnadnění navigace WPF implementuje následující:  
  
- <xref:System.Windows.Navigation.NavigationService>sdílený navigační modul pro zpracování žádostí o navigaci, které jsou používány <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Navigation.NavigationWindow>a XBAP k podpoře navigace uvnitř aplikace.  
  
- Navigační metody pro zahájení navigace  
  
- Navigační události pro sledování a interakci s dobou života navigace  
  
- Zapamatování navigace zpět a přeposlání pomocí deníku, který lze také kontrolovat a manipulovat.  
  
 Informace najdete v tématu [Přehled navigace](navigation-overview.md).  
  
 WPF také podporuje speciální typ navigace známý jako strukturovaná navigace. Strukturované navigace lze použít k volání jedné nebo více stránek, které vracejí data strukturovaným a předvídatelným způsobem, který je konzistentní s voláním funkce. Tato funkce závisí na třídě <xref:System.Windows.Navigation.PageFunction%601>, která je podrobněji popsána v [přehledu strukturované navigace](structured-navigation-overview.md). <xref:System.Windows.Navigation.PageFunction%601> také slouží ke zjednodušení vytváření komplexních navigačních topologií, které jsou popsány v tématu [Přehled topologií navigace](navigation-topologies-overview.md).  
  
<a name="Hosting"></a>   
## <a name="hosting"></a>Hosting  
 Aplikace XBAP je možné hostovat v aplikacích Microsoft Internet Explorer a Firefox. Každý model hostování má vlastní sadu důležitých informací a omezení, které jsou pokryty v [hostování](hosting-wpf-applications.md).  
  
<a name="Build_and_Deploy"></a>   
## <a name="build-and-deploy"></a>Sestavení a nasazení  
 I když jednoduché aplikace WPF mohou být sestaveny z příkazového řádku pomocí kompilátorů příkazového řádku, WPF se integruje se sadou Visual Studio a poskytuje další podporu, která zjednodušuje proces vývoje a sestavování. Další informace naleznete v tématu [sestavování aplikace WPF](building-a-wpf-application-wpf.md).  
  
 V závislosti na typu aplikace, kterou sestavíte, existuje jedna nebo více možností nasazení, ze kterých si můžete vybrat. Další informace naleznete v tématu [nasazení aplikace WPF](deploying-a-wpf-application-wpf.md).  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled správy aplikací](application-management-overview.md)|Poskytuje přehled <xref:System.Windows.Application> třídy, včetně správy životního cyklu aplikací, Windows, prostředků aplikací a navigace.|  
|[Windows ve WPF](windows-in-wpf-applications.md)|Obsahuje podrobnosti o správě oken ve vaší aplikaci, včetně způsobu použití <xref:System.Windows.Window> třídy a dialogových oken.|  
|[Přehled navigace](navigation-overview.md)|Poskytuje přehled o správě navigace mezi stránkami aplikace.|  
|[Hostování](hosting-wpf-applications.md)|Poskytuje přehled aplikací prohlížeče XAML (XBAP).|  
|[Sestavení a nasazení](building-and-deploying-wpf-applications.md)|Popisuje, jak sestavit a nasadit vaši aplikaci WPF.|  
|[Úvod k použití WPF v sadě Visual Studio](../getting-started/introduction-to-wpf-in-vs.md)|Popisuje hlavní funkce WPF.|  
|[Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|Návod, který ukazuje, jak vytvořit aplikaci WPF pomocí navigace na stránce, rozložení, ovládacích prvků, obrázků, stylů a vazeb.|
