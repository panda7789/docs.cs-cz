---
title: Určení místa, kde aplikace My. Application. Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 305c29e33f6cd421f39004e09d27c75b02ba8354
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912559"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Určení místa, kde aplikace My. Application. Log zapisuje informace (Visual Basic)

`My.Application.Log` Objekt může zapisovat informace do několika posluchačů protokolů. Naslouchací procesy protokolu jsou nakonfigurovány pomocí konfiguračního souboru počítače a mohou být přepsány konfiguračním souborem aplikace. Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.

Další informace o výchozích umístěních výstupu najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Určení naslouchacího procesu pro My. Application. log

1. Vyhledejte konfigurační soubor sestavení. Pokud vyvíjíte sestavení, můžete získat přístup k souboru App. config v aplikaci Visual Studio z **Průzkumník řešení**. V opačném případě je název konfiguračního souboru názvem sestavení připojeným pomocí ". config" a je umístěn ve stejném adresáři jako sestavení.

    > [!NOTE]
    > Ne každé sestavení má konfigurační soubor.

    Konfigurační soubor je soubor XML.

2. Vyhledejte část v části s `name` atributem "DefaultSource", který se nachází v části.`<sources>` `<source>` `<listeners>` Oddíl je umístěný `<system.diagnostics>` v části v části nejvyšší úrovně `<configuration>`. `<sources>`

    Pokud tyto oddíly neexistují, může konfigurační soubor počítače nakonfigurovat `My.Application.Log` naslouchací procesy protokolu. Následující postup popisuje, jak určit, jaký konfigurační soubor počítače definuje:

    1. Vyhledejte soubor Machine. config počítače. Obvykle se nachází v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , kde `SystemRoot` je adresář operačního systému, a `frameworkVersion` je verze .NET Framework.

        Nastavení v souboru Machine. config může přepsat konfigurační soubor aplikace.

        Pokud volitelné prvky uvedené níže neexistují, můžete je vytvořit.

    2. `name` `<system.diagnostics>` `<configuration>` `<sources>` Vyhledejte část v`<source>` části s atributem "DefaultSource" v části v části v části v sekci nejvyšší úrovně. `<listeners>`

        Pokud tyto oddíly neexistují, pak `My.Application.Log` má pouze výchozí naslouchací procesy protokolu.

3. V části <`add>` `listeners>` vyhledejte prvky <.

     Tyto prvky přidávají pojmenované naslouchací procesy protokolu `My.Application.Log` ke zdroji.

4. Vyhledejte prvky s názvy naslouchacího procesu protokolu `<sharedListeners>` v části `<system.diagnostics>` v části v oddílu nejvyšší úrovně `<configuration>`. `<add>`

5. Pro mnoho typů sdílených posluchačů obsahuje inicializační data naslouchacího procesu popis, kde naslouchací proces přesměruje data:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> Naslouchací proces zapisuje do protokolu souborů, jak je popsáno v úvodu.

    - Naslouchací proces zapisuje informace do protokolu událostí počítače určeného `initializeData` parametrem. <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

    - Naslouchací procesy <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>azapisují do souboru zadaného v `initializeData` parametru. <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> Naslouchací proces zapisuje do konzoly příkazového řádku.

    - Informace o tom, kde jiné typy protokolových posluchačů zapisují informace, najdete v dokumentaci k tomuto typu.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolovat výjimky](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md)
- [Odstraňování potíží: Protokoly naslouchacího procesu](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
