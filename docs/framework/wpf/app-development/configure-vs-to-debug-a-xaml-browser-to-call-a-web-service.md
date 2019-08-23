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
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958688"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Postupy: Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Spouštějte v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezený na sadu oprávnění pro internetovou zónu. Tato sada oprávnění omezuje volání webové služby pouze na webové služby, které jsou umístěny v [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] lokalitě aplikace původu. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Při ladění z aplikace Visual Studio 2005 se ale nepovažuje za stejný web jako webová služba, na kterou odkazuje. Tím dojde k vyvolání výjimek zabezpečení při [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] pokusu o volání webové služby. Projekt sady Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] však lze nakonfigurovat tak, aby simuloval stejný web jako Web Service, který při ladění volá. To umožňuje [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpečné volání webové služby, aniž by došlo k výjimkám zabezpečení.

## <a name="configuring-visual-studio"></a>Konfigurování sady Visual Studio
 Konfigurace sady [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Visual Studio 2005 pro ladění volání webové služby:

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program** a zadejte následující:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. V části **Možnosti spuštění** zadejte do textového pole **argumenty příkazového řádku** následující text:

     `-debug`  *Bitmap*

     Hodnota *filename* pro parametr **-Debug** je název souboru. XBAP; například:

     `-debug c:\example.xbap`

> [!NOTE]
> Toto je výchozí konfigurace pro řešení, která jsou vytvořena pomocí šablony projektu sady Visual [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] Studio 2005.

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **Možnosti spuštění** přidejte do textového pole **argumenty příkazového** řádku následující parametr příkazového řádku:

     `-debugSecurityZoneURL`  *ADRESA URL*

     [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] Hodnota *URL* pro parametr **-debugSecurityZoneURL** je pro umístění, které chcete simulovat jako web počátku aplikace.

 Zvažte příklad [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] , který používá webovou službu s následujícími [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]možnostmi:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Lokalita původu [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] této webové služby je:

 `http://services.msdn.microsoft.com`

 V důsledku toho parametr a hodnota příkazového řádku Complete **-debugSecurityZoneURL** je:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Viz také:

- [Hostitel WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
