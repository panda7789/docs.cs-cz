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
ms.openlocfilehash: 7730ab452e227b11e5a9dd69cdabec51f333ce4f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321202"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] běží v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezený na sadu oprávnění pro internetovou zónu. Tato sada oprávnění omezuje volání webové služby pouze na webové služby, které jsou umístěny v lokalitě aplikace [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] původu. Když je [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Laděna ze sady Visual Studio 2005, nepovažuje se za stejný web jako webová služba, na kterou odkazuje. To způsobí, že výjimky zabezpečení budou vyvolány, když se [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusí zavolat webovou službu. Projekt sady Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] se však dá nakonfigurovat tak, aby simuloval stejný web jako Web Service, který při ladění volá. To umožňuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečně volat webovou službu, aniž by došlo k výjimkám zabezpečení.

## <a name="configuring-visual-studio"></a>Konfigurování sady Visual Studio
 Konfigurace sady Visual Studio 2005 pro ladění [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], která volá webovou službu:

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program** a zadejte následující:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. V části **Možnosti spuštění** zadejte do textového pole **argumenty příkazového řádku** následující text:

     `-debug`  *název_souboru*

     Hodnota *filename* pro parametr **-Debug** je název souboru. XBAP; například:

     `-debug c:\example.xbap`

> [!NOTE]
> Toto je výchozí konfigurace pro řešení, která jsou vytvořena pomocí šablony projektu [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] sady Visual Studio 2005.

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **Možnosti spuštění** přidejte do textového pole **argumenty příkazového** řádku následující parametr příkazového řádku:

     `-debugSecurityZoneURL`  *Adresa URL*

     Hodnota *URL* pro parametr **-debugSecurityZoneURL** je adresa URL pro umístění, které chcete simulovat jako web počátku aplikace.

 Zvažte například [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], který používá webovou službu s následující adresou URL:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Adresa URL místa původu této webové služby je:

 `http://services.msdn.microsoft.com`

 V důsledku toho parametr a hodnota příkazového řádku Complete **-debugSecurityZoneURL** je:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Viz také:

- [Hostitel WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
