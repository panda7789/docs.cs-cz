---
title: Zjištění, kam objekt My.Application.Log zapisuje informace
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398276"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)

`My.Application.Log`Objekt může zapisovat informace do několika posluchačů protokolů. Naslouchací procesy protokolu jsou nakonfigurovány pomocí konfiguračního souboru počítače a mohou být přepsány konfiguračním souborem aplikace. Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.

Další informace o výchozích umístěních výstupu najdete v tématu [práce s protokoly aplikací](working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Určení naslouchacího procesu pro My. Application. log

1. Vyhledejte konfigurační soubor sestavení. Pokud vyvíjíte sestavení, můžete získat přístup k souboru App. config v aplikaci Visual Studio z **Průzkumník řešení**. V opačném případě je název konfiguračního souboru názvem sestavení připojeným pomocí ". config" a je umístěn ve stejném adresáři jako sestavení.

    > [!NOTE]
    > Ne každé sestavení má konfigurační soubor.

    Konfigurační soubor je soubor XML.

2. Vyhledejte `<listeners>` část v části `<source>` s `name` atributem "DefaultSource", který se nachází v `<sources>` části. `<sources>`Oddíl je umístěný v části `<system.diagnostics>` v části nejvyšší úrovně `<configuration>` .

    Pokud tyto oddíly neexistují, může konfigurační soubor počítače nakonfigurovat `My.Application.Log` naslouchací procesy protokolu. Následující postup popisuje, jak určit, jaký konfigurační soubor počítače definuje:

    1. Vyhledejte soubor Machine. config počítače. Obvykle se nachází v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , kde `SystemRoot` je adresář operačního systému, a `frameworkVersion` je verze .NET Framework.

        Nastavení v souboru Machine. config může přepsat konfigurační soubor aplikace.

        Pokud volitelné prvky uvedené níže neexistují, můžete je vytvořit.

    2. Vyhledejte část v části `<listeners>` `<source>` s `name` atributem "DefaultSource" v části v části v části v sekci `<sources>` `<system.diagnostics>` nejvyšší úrovně `<configuration>` .

        Pokud tyto oddíly neexistují, pak `My.Application.Log` má pouze výchozí naslouchací procesy protokolu.

3. `add>`V části <vyhledejte prvky <`listeners>` .

     Tyto prvky přidávají pojmenované naslouchací procesy protokolu ke `My.Application.Log` zdroji.

4. Vyhledejte `<add>` prvky s názvy naslouchacího procesu protokolu v části v části v oddílu `<sharedListeners>` `<system.diagnostics>` nejvyšší úrovně `<configuration>` .

5. Pro mnoho typů sdílených posluchačů obsahuje inicializační data naslouchacího procesu popis, kde naslouchací proces přesměruje data:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje do protokolu souborů, jak je popsáno v úvodu.

    - <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje informace do protokolu událostí počítače určeného `initializeData` parametrem. Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Naslouchací procesy a zapisují do souboru zadaného v `initializeData` parametru.

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Naslouchací proces zapisuje do konzoly příkazového řádku.

    - Informace o tom, kde jiné typy protokolových posluchačů zapisují informace, najdete v dokumentaci k tomuto typu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Práce s protokoly aplikací](working-with-application-logs.md)
- [Postupy: Protokolování výjimek](how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](walkthrough-changing-where-my-application-log-writes-information.md)
- [Události Trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md)
- [Řešení potíží: Komponenty naslouchající protokolům](troubleshooting-log-listeners.md)
