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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353610"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)

Objekt `My.Application.Log` může zapisovat informace do několika posluchačů protokolů. Naslouchací procesy protokolu jsou nakonfigurovány pomocí konfiguračního souboru počítače a mohou být přepsány konfiguračním souborem aplikace. Toto téma popisuje výchozí nastavení a způsob určení nastavení aplikace.

Další informace o výchozích umístěních výstupu najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Určení naslouchacího procesu pro My. Application. log

1. Vyhledejte konfigurační soubor sestavení. Pokud vyvíjíte sestavení, můžete získat přístup k souboru App. config v aplikaci Visual Studio z **Průzkumník řešení**. V opačném případě je název konfiguračního souboru názvem sestavení připojeným pomocí ". config" a je umístěn ve stejném adresáři jako sestavení.

    > [!NOTE]
    > Ne každé sestavení má konfigurační soubor.

    Konfigurační soubor je soubor XML.

2. Vyhledejte část `<listeners>` v části `<source>` s atributem `name` "DefaultSource", který se nachází v části `<sources>`. Část `<sources>` se nachází v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

    Pokud tyto oddíly neexistují, může konfigurační soubor počítače nakonfigurovat naslouchací procesy protokolu `My.Application.Log`. Následující postup popisuje, jak určit, jaký konfigurační soubor počítače definuje:

    1. Vyhledejte soubor Machine. config počítače. Obvykle se nachází v adresáři *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , kde je `SystemRoot` adresářem operačního systému a `frameworkVersion` je verze .NET Framework.

        Nastavení v souboru Machine. config může přepsat konfigurační soubor aplikace.

        Pokud volitelné prvky uvedené níže neexistují, můžete je vytvořit.

    2. Vyhledejte část `<listeners>` v části `<source>` s atributem `name` "DefaultSource" v části pro `<sources>` v sekci `<system.diagnostics>` na nejvyšší úrovni.`<configuration>`

        Pokud tyto oddíly neexistují, `My.Application.Log` mají pouze výchozí naslouchací procesy protokolu.

3. V části <`listeners>` vyhledejte prvky`add>` <.

     Tyto prvky přidají pojmenované naslouchací procesy protokolu do zdroje `My.Application.Log`.

4. Vyhledejte prvky `<add>` s názvy naslouchacího procesu protokolu v části `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

5. Pro mnoho typů sdílených posluchačů obsahuje inicializační data naslouchacího procesu popis, kde naslouchací proces přesměruje data:

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do protokolu souborů, jak je popsáno v úvodu.

    - Naslouchací proces <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> zapisuje informace do protokolu událostí počítače určeného parametrem `initializeData`. Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

    - Naslouchací procesy <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisují do souboru zadaného v parametru `initializeData`.

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do konzoly příkazového řádku.

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
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md)
- [Řešení potíží: Součásti naslouchající protokolům](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
