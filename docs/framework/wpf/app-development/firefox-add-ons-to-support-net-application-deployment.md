---
title: Doplňky Firefox pro podporu nasazení .NET aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 837ed1cd41869031e8c0b549ffcd26e3285570cd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368061"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Doplňky Firefox pro podporu nasazení .NET aplikací
Povolit Windows Presentation Foundation (WPF) modul plugin pro Firefox a rozhraní .NET Framework Pomocníka pro Firefox [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)], dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a aplikací ClickOnce pro práci s prohlížeči Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Modul plugin WPF pro Firefox  
 Umožňuje modulu Plugin WPF pro Firefox [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] a dojde ke ztrátě [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů přejde a spusťte na nejvyšší úrovni nebo v elementu IFRAME HTML v prohlížeči Firefox. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikaci, která můžete publikovat na webový server a spouští v rámci podporovaných prohlížečích. Přijít o provedené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor pouze pro XAML, který je možné přejde a zobrazí v podporovaných prohlížečích, podobně jako soubor XML.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Modul plugin pro Firefox se instaluje s [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Zahrnuje Windows 7 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], ale nezahrnuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modul plugin pro Firefox. Nelze nainstalovat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modul plugin pro Firefox ve Windows 7.  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] Nezahrnuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modul plugin pro Firefox. Ale pokud mají oba [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] jsou nainstalovány, modulu Plugin WPF pro Firefox se instaluje s [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]. Proto [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] aplikace bude stále spuštěn, protože hostitel WPF se načtou správnou verzi rozhraní framework. Další informace najdete v tématu [hostitel WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework – pomocník pro Firefox  
 Rozhraní .NET Framework Pomocník pro Firefox umožňuje samostatných aplikací ClickOnce pro spuštění z prohlížeče Firefox. Rozhraní .NET Framework Pomocníka pro Firefox funkce stejně jako v případě, že je nainstalována před a po prohlížeče Firefox. Když se spustí prohlížeč Firefox a [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] je nainstalována, Firefox vyhledá a nainstaluje rozhraní .NET Framework Pomocník pro Firefox. Uživatelé můžou konfigurovat rozhraní .NET Framework Pomocník pro Firefox provést následující kroky:  
  
-   Dotázat se před spuštěním aplikace ClickOnce.  
  
-   Sestavy všech nainstalovaných verzí rozhraní .NET Framework nebo jenom na nejnovější verzi.  
  
 Rozhraní .NET Framework Pomocník pro Firefox je součástí [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]. Informace o odebrání rozhraní .NET Framework Pomocník pro Firefox, naleznete v tématu [odebrání rozhraní .NET Framework Pomocník pro Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Viz také:
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
- [Přehled aplikací Prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md)
- [Zjištění, jestli je instalovaný modulu plugin WPF pro Firefox](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
