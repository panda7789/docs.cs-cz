---
title: Doplňky Firefox pro podporu nasazení .NET aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: f05f5afa0c0a7ef858442bd98233865834b8b89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547440"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Doplňky Firefox pro podporu nasazení .NET aplikací
Povolit systému Windows Presentation Foundation (WPF) modul plug-in pro Firefox a rozhraní .NET Framework Pomocníka pro Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], přijít [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a aplikace ClickOnce pro práci s prohlížeči Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Modul Plug-in pro Firefox WPF  
 Modul plug-in pro Firefox WPF umožňuje [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a ztratit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů přešli a spustit v elementu IFRAME HTML v prohlížeči Firefox nebo na nejvyšší úrovni. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, která umožňuje publikovat na webový server a spouští v rámci podporované prohlížeče. Uvolněná [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor jen XAML, který můžete přešli a zobrazit v podporovaných prohlížečích, podobně jako soubor XML.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Modul plug-in pro Firefox se instaluje s [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Okno 7 zahrnuje [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ale nezahrnuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modulu plug-in pro Firefox. Nelze nainstalovat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modulu plug-in pro Firefox na systému Windows 7.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Nezahrnuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modulu plug-in pro Firefox. Ale pokud obě [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] jsou nainstalovaná, modul plug-in pro Firefox WPF se instaluje s [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Proto [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] aplikace bude pořád spustit, protože hostitel WPF načte správnou verzi rozhraní. Další informace najdete v tématu [WPF hostitele (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework – pomocník pro Firefox  
 Rozhraní .NET Framework Pomocníka pro Firefox umožňuje samostatných aplikací ClickOnce pro spouštění z prohlížeče Firefox. Rozhraní .NET Framework Pomocníka pro funkce Firefox, stejně jako při instalaci před a po prohlížeče Firefox. Při spuštění prohlížeče Firefox a [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] je nainstalovaná, Firefox vyhledá a nainstaluje rozhraní .NET Framework Pomocníka pro Firefox. Uživatele můžete nakonfigurovat na rozhraní .NET Framework Pomocníka pro Firefox provést následující akce:  
  
-   Před spuštěním aplikace ClickOnce výzvu.  
  
-   Vytvoření sestavy všech nainstalovaných verzí rozhraní .NET Framework nebo jenom na nejnovější verzi.  
  
 Rozhraní .NET Framework Pomocníka pro Firefox je součástí [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Informace o odebrání rozhraní .NET Framework Pomocníka pro Firefox najdete v tématu [jak odebrat rozhraní .NET Framework Pomocníka pro Firefox](http://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [Přehled aplikací Prohlížeče WPF XAML](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Zjištění, jestli je instalovaný modulu plugin WPF pro Firefox](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
