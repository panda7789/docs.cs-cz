---
title: 'Postupy: Zápis do protokolu událostí aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352051"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)

Objekty a `My.Application.Log` `My.Log` můžete použít k zápisu informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak nakonfigurovat `My.Application.Log` naslouchací proces protokolu událostí, takže zapíše informace o trasování do protokolu událostí aplikace.

Do protokolu zabezpečení nelze zapisovat. Chcete-li zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo Administrator.

Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**. Další informace naleznete [v tématu ETW Události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace posluchače protokolu událostí

1. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.

    \-nebo -

    Pokud není k dispozici žádný soubor app.config,

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Vyhledejte `<listeners>` oddíl v konfiguračním souboru aplikace.

    Oddíl najdete `<listeners>` v `<source>` sekci s atributem název "DefaultSource", který `<system.diagnostics>` je vnořen pod oddíl, který je vnořen pod oddíl nejvyšší úrovně. `<configuration>`

3. Přidejte tento `<listeners>` prvek do tohoto oddílu:

    ```xml
    <add name="EventLog"/>
    ```

4. Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.

5. Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Nahraďte `APPLICATION_NAME` název aplikace.

    > [!NOTE]
    > Aplikace obvykle zapisuje pouze chyby do protokolu událostí. Informace o výstupu protokolu filtrování naleznete [v tématu Návod: Filtrování výstupu my.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o událostech do protokolu událostí

Pomocí `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` or zapište informace do protokolu událostí. Další informace naleznete v [tématu How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po konfiguraci posluchače protokolu událostí pro sestavení obdrží `My.Application.Log` všechny zprávy, které zapisuje z tohoto sestavení.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
