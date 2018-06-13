---
title: 'Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: 948a730185650cb3449202503a049e9caff7c4bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547496"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] Spusťte v rámci částečným vztahem důvěryhodnosti zabezpečení izolovaného prostoru, který je omezen na sadu oprávnění pro zónu Internetu. Omezuje volání webové služby k jenom webové služby, které jsou umístěné v této sadě oprávnění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] serveru aplikace původu. Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je ladit z [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], i když není to považováno za tak, aby měl stejné lokalitě původu jako webové služby odkazy. Této výjimky zabezpečení příčiny vyvolá, když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí volání webové služby. Ale [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu lze nakonfigurovat k simulaci s ke stejné lokalitě jako webovou službu zavolá při ladění původu. To umožňuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu bez způsobení výjimky zabezpečení.  
  
## <a name="configuring-visual-studio"></a>Konfigurace sady Visual Studio  
 Ke konfiguraci [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] k ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] webové služby, který volá:  
  
1.  S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrhář projektu**, klikněte **ladění** kartě.  
  
3.  V **spustit akci** vyberte **počáteční vnějšímu programu** a zadejte následující:  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  V **možnosti spuštění** zadejte následující kód do **argumenty příkazového řádku** textového pole:  
  
     `-debug`  *Název souboru*  
  
     *Filename* hodnota **– ladění** parametr je název souboru .xbap; například:  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  Toto je výchozí konfiguraci pro řešení, které jsou vytvořené pomocí [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] šablona projektu.  
  
1.  S projekt vybraný v **Průzkumníku řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  V **Návrhář projektu**, klikněte **ladění** kartě.  
  
3.  V **možnosti spuštění** přidejte následující parametr příkazového řádku k **argumenty příkazového řádku** textového pole:  
  
     `-debugSecurityZoneURL`  *ADRESA URL*  
  
     *URL* hodnota **- debugSecurityZoneURL** parametr je [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pro umístění, které chcete simulovat jako webu původu vaší aplikace.  
  
 Jako příklad, zvažte [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] používající webové služby s následující [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 Místo původu [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pro tento Web je služba:  
  
 `http://services.msdn.microsoft.com`  
  
 V důsledku toho dokončení **- debugSecurityZoneURL** parametr příkazového řádku a hodnota je:  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a>Viz také  
 [Hostitel WPF (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
