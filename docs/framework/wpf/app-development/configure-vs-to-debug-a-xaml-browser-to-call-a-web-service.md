---
title: 'Postupy: Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314370"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Postupy: Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] Spusťte v sandboxu částečným vztahem důvěryhodnosti zabezpečení, který je omezena na sadu oprávnění pro zónu Internetu. Tato sada oprávnění omezuje pouze webové služby, které se nacházejí ve volání webové služby [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikace webovou stránku původu. Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ladění ze sady Visual Studio 2005, ale není považováno za používat webová služba odkazy na stejné místo původu. Výjimky zabezpečení Toto způsobí, že při vyvolání [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí o volání webové služby. Nicméně Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu lze nastavit pro simulaci s původu stejné lokalitě jako webové služby, které volá při ladění. Díky tomu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu bez způsobení výjimky zabezpečení.

## <a name="configuring-visual-studio"></a>Konfigurace nástroje Visual Studio
 Konfigurace sady Visual Studio 2005 pro ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , která volá webové služby:

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. V **Návrháře projektu**, klikněte na tlačítko **ladění** kartu.

3. V **spustit akci** vyberte **externí program Start** a zadejte následující:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. V **možnosti spuštění** části, zadejte následující kód do **argumenty příkazového řádku** textové pole:

     `-debug`  *filename*

     *Filename* hodnota **– ladění** parametr je název souboru .xbap; například:

     `-debug c:\example.xbap`

> [!NOTE]
>  Toto je výchozí konfigurace pro řešení, které jsou vytvořeny pomocí Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] šablony projektu.

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. V **Návrháře projektu**, klikněte na tlačítko **ladění** kartu.

3. V **možnosti spuštění** části, přidejte následující parametr příkazového řádku **argumenty příkazového řádku** textové pole:

     `-debugSecurityZoneURL`  *Adresa URL*

     *Adresy URL* hodnota **- debugSecurityZoneURL** parametr je [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pro umístění, které chcete simulovat jako místo původu vaší aplikace.

 Jako příklad, vezměte v úvahu [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] webovou službu, která používá následující [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Umístění původních [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pro tento Web service je:

 `http://services.msdn.microsoft.com`

 V důsledku toho kompletní **- debugSecurityZoneURL** parametr příkazového řádku a hodnota je:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Viz také:

- [Hostitel WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
