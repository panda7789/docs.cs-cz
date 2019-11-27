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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352051"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)

Objekty `My.Application.Log` a `My.Log` lze použít k zápisu informací o událostech, ke kterým dojde v aplikaci. Tento příklad ukazuje, jak nakonfigurovat naslouchací proces protokolu událostí tak, `My.Application.Log` zapisuje trasovací informace do protokolu událostí aplikace.

Do protokolu zabezpečení nelze zapisovat. Aby bylo možné zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo správce.

Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu událostí

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

    \- nebo-

    Pokud soubor App. config neexistuje,

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Přidat**.

2. V konfiguračním souboru aplikace vyhledejte část `<listeners>`.

    Část `<listeners>` najdete v části `<source>` s názvem "DefaultSource", který je vnořen do oddílu `<system.diagnostics>`, který je vnořený pod oddílem `<configuration>` nejvyšší úrovně.

3. Přidejte tento prvek do tohoto `<listeners>` části:

    ```xml
    <add name="EventLog"/>
    ```

4. Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>` v části `<configuration>` nejvyšší úrovně.

5. Přidejte tento prvek do tohoto `<sharedListeners>` části:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Nahraďte `APPLICATION_NAME` názvem vaší aplikace.

    > [!NOTE]
    > Aplikace obvykle zapisuje pouze chyby do protokolu událostí. Informace o filtrování výstupu protokolu naleznete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o události do protokolu událostí

Pomocí metody `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` zapište informace do protokolu událostí. Další informace naleznete v tématu [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po nakonfigurování naslouchacího procesu protokolu událostí pro sestavení obdrží všechny zprávy, které `My.Application.Log` zápisy z tohoto sestavení.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
