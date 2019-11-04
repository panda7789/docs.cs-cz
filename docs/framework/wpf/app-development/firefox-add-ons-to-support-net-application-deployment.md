---
title: Doplňky Firefox pro podporu nasazení .NET aplikací
ms.date: 03/30/2017
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
ms.openlocfilehash: 6e8a333fc84eb85b7a312cb87207ebc235fbfe9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424561"
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>Doplňky Firefox pro podporu nasazení .NET aplikací
Modul plug-in Windows Presentation Foundation (WPF) pro Firefox a pomocníka .NET Framework pro prohlížeč Firefox povoluje aplikace prohlížeče XAML (XBAP), volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a aplikace ClickOnce pro práci s prohlížečem Mozilla Firefox.  
  
## <a name="wpf-plug-in-for-firefox"></a>Modul plug-in WPF pro Firefox  
 Modul plug-in WPF pro Firefox umožňuje XBAP a volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, které se mají přejít na nejvyšší úroveň nebo v prvku HTML IFRAME v prohlížeči Firefox. XBAP je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, která se dá publikovat na webovém serveru a spustit v podporovaných prohlížečích. Volný [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je soubor pouze v jazyce XAML, který lze přejít na a zobrazit v podporovaných prohlížečích, podobně jako soubor XML.  
  
 Modul plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro Firefox se instaluje s .NET Framework 3,5. Okno 7 obsahuje .NET Framework 3,5, ale neobsahuje modul plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro Firefox. Nemůžete nainstalovat modul plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro Firefox ve Windows 7.  
  
 .NET Framework 4 neobsahují modul plug-in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pro Firefox. Pokud však jsou nainstalovány .NET Framework 3,5 i .NET Framework 4, modul plug-in WPF pro Firefox je nainstalován s .NET Framework 3,5. Proto budou aplikace .NET Framework 4 stále spuštěny, protože hostitel WPF načte správnou verzi rozhraní. Další informace najdete v tématu [hostitel WPF (PresentationHost. exe)](wpf-host-presentationhost-exe.md).  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework – pomocník pro Firefox  
 Pomocník pro .NET Framework pro Firefox umožňuje spouštět samostatné aplikace ClickOnce z prohlížeče Firefox. Pomocník pro .NET Framework pro Firefox funguje identicky, když je nainstalován před a po prohlížeči Firefox. Když se spustí prohlížeč Firefox a nainstalují se .NET Framework 3,5 SP1, aplikace Firefox najde a nainstaluje pomocníka .NET Framework pro Firefox. Uživatelé můžou nakonfigurovat pomocníka .NET Framework pro Firefox, aby provede následující:  
  
- Před spuštěním aplikace ClickOnce se zobrazí výzva.  
  
- Ohlaste všechny nainstalované verze .NET Framework nebo jenom nejnovější verzi.  
  
 Pomocník pro .NET Framework pro Firefox je součástí .NET Framework 3,5 SP1. Informace o odebrání pomocníka .NET Framework pro Firefox najdete v tématu [Odebrání pomocníka .NET Framework pro prohlížeč Firefox](https://go.microsoft.com/fwlink/?LinkId=177944).  
  
## <a name="see-also"></a>Viz také:

- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
- [Přehled aplikací Prohlížeče WPF XAML](wpf-xaml-browser-applications-overview.md)
- [Zjištění, jestli je instalovaný modulu plugin WPF pro Firefox](how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
