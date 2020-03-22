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
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353610"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)

Objekt `My.Application.Log` může zapisovat informace do několika naslouchacích procesů protokolu. Naslouchací procesy protokolu jsou konfigurovány konfiguračním souborem počítače a mohou být přepsány konfiguračním souborem aplikace. Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.

Další informace o výchozích výstupních umístěních naleznete v [tématu Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Chcete-li určit posluchače pro My.Application.Log

1. Vyhledejte konfigurační soubor sestavení. Pokud vyvíjíte sestavení, můžete získat přístup k app.config v sadě Visual Studio z **Průzkumníka řešení**. V opačném případě je název konfiguračního souboru název sestavení připojen s ".config" a je umístěn ve stejném adresáři jako sestavení.

    > [!NOTE]
    > Ne každé sestavení má konfigurační soubor.

    Konfigurační soubor je soubor XML.

2. Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource", který se nachází v `<sources>` sekci. Sekce `<sources>` je umístěna `<system.diagnostics>` v sekci, v `<configuration>` sekci nejvyšší úrovně.

    Pokud tyto oddíly neexistují, může konfigurační `My.Application.Log` soubor počítače konfigurovat posluchače protokolu. Následující kroky popisují, jak určit, co definuje konfigurační soubor počítače:

    1. Vyhledejte soubor machine.config počítače. Obvykle je umístěn v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG,* kde `SystemRoot` je adresář `frameworkVersion` operačního systému a je verzí rozhraní .NET Framework.

        Nastavení v souboru machine.config lze přepsat konfiguračním souborem aplikace.

        Pokud níže uvedené volitelné prvky neexistují, můžete je vytvořit.

    2. Vyhledejte `<listeners>` oddíl v `<source>` části `name` s atributem "DefaultSource" v `<sources>` `<system.diagnostics>` části, v sekci, `<configuration>` v části nejvyšší úrovně.

        Pokud tyto oddíly neexistují, `My.Application.Log` pak má pouze výchozí naslouchací procesy protokolu.

3. Vyhledejte `add>` <prvky `listeners>` v části <.

     Tyto prvky přidat pojmenované `My.Application.Log` posluchače protokolu do zdroje.

4. Vyhledejte `<add>` prvky s názvy posluchačů `<sharedListeners>` protokolu v `<system.diagnostics>` části, v části, v části nejvyšší úrovně. `<configuration>`

5. Pro mnoho typů sdílených naslouchacích procesů inicializační data posluchače obsahuje popis, kde posluchač směruje data:

    - Naslouchací <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> proces zapíše do protokolu souborů, jak je popsáno v úvodu.

    - Naslouchací <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> proces zapisuje informace do protokolu událostí počítače určeného parametrem. `initializeData` Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**. Další informace naleznete [v tématu ETW Události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Posluchači <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> a zapisovat do `initializeData` souboru určeného v parametru.

    - Naslouchací <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> proces zapisuje do konzoly příkazového řádku.

    - Informace o tom, kde jiné typy posluchačů protokolu psát informace, naleznete v dokumentaci tohoto typu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Události Trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md)
- [Řešení potíží: Součásti naslouchající protokolům](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
