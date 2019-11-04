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
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460902"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Postupy: Konfigurace aplikace Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby
Aplikace prohlížeče XAML (XBAP) se spouštějí v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezený na sadu oprávnění pro internetovou zónu. Tato sada oprávnění omezuje volání webové služby pouze na webové služby, které jsou umístěny v lokalitě aplikace XBAP o původu. Když je aplikace XBAP Laděna ze sady Visual Studio 2005, ale není považována za stejnou lokalitu jako webová služba, na kterou odkazuje. To způsobí, že výjimky zabezpečení budou vyvolány, když se XBAP pokusí zavolat webovou službu. Projekt aplikace Visual Studio 2005 XAML (WPF) se však dá nakonfigurovat tak, aby simuloval se stejným webem jako s webovou službou, kterou volá při ladění. To umožňuje, aby XBAP bezpečně volala webovou službu, aniž by docházelo k výjimkám zabezpečení.

## <a name="configuring-visual-studio"></a>Konfigurování sady Visual Studio
 Konfigurace sady Visual Studio 2005 pro ladění XBAP, která volá webovou službu:

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **spouštěcí akce** vyberte **spustit externí program** a zadejte následující:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. V části **Možnosti spuštění** zadejte do textového pole **argumenty příkazového řádku** následující text:

     `-debug`  *název_souboru*

     Hodnota *filename* pro parametr **-Debug** je název souboru. XBAP; například:

     `-debug c:\example.xbap`

> [!NOTE]
> Toto je výchozí konfigurace pro řešení vytvořená pomocí šablony projektu aplikace Visual Studio 2005 XAML (WPF).

1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.

2. V **Návrháři projektu**klikněte na kartu **ladění** .

3. V části **Možnosti spuštění** přidejte do textového pole **argumenty příkazového** řádku následující parametr příkazového řádku:

     `-debugSecurityZoneURL`  *Adresa URL*

     Hodnota *URL* pro parametr **-debugSecurityZoneURL** je adresa URL pro umístění, které chcete simulovat jako web počátku aplikace.

 Zvažte například aplikaci prohlížeče XAML (XBAP), která používá webovou službu s následující adresou URL:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Adresa URL místa původu této webové služby je:

 `http://services.msdn.microsoft.com`

 V důsledku toho parametr a hodnota příkazového řádku Complete **-debugSecurityZoneURL** je:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Viz také:

- [Hostitel WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
