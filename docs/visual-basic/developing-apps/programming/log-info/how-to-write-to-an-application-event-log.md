---
title: 'Postupy: Zápis do protokolu událostí aplikace (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 385a85d956a0de727e3c061ec447a3d53ad6c159
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054149"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)

Pomocí `My.Application.Log` objektů a `My.Log` můžete zapisovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak nakonfigurovat naslouchací proces protokolu událostí, `My.Application.Log` který zapisuje trasovací informace do protokolu událostí aplikace.

Do protokolu zabezpečení nelze zapisovat. Aby bylo možné zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo správce.

Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu událostí

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

    \- nebo –

    Pokud soubor App. config neexistuje,

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. `<listeners>` Vyhledejte část v konfiguračním souboru aplikace.

    `<listeners>` Část `<system.diagnostics>` `<configuration>` v oddílu najdete s názvem atribut "DefaultSource", který je vnořen do oddílu, který je vnořen v části nejvyšší úrovně. `<source>`

3. Přidejte tento element do této `<listeners>` části:

    ```xml
    <add name="EventLog"/>
    ```

4. `<sharedListeners>` Vyhledejte část `<system.diagnostics>` v části v sekci nejvyšší úrovně `<configuration>` .

5. Přidejte tento element do této `<sharedListeners>` části:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Nahraďte `APPLICATION_NAME` názvem vaší aplikace.

    > [!NOTE]
    > Aplikace obvykle zapisuje pouze chyby do protokolu událostí. Informace o filtrování výstupu protokolu najdete v tématu [Názorný postup: Vyfiltruje se výstup](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)my. Application. log.

## <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o události do protokolu událostí

Pomocí metody `My.Application.Log.WriteException` nebo zapište informace do protokolu událostí. `My.Application.Log.WriteEntry` Další informace najdete v tématu [jak: Pište zprávy](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) protokolu a [postupy: Protokoluje](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)výjimky.

Po nakonfigurování naslouchacího procesu protokolu událostí pro sestavení obdrží všechny zprávy, které `My.Application.Log` zapisují z tohoto sestavení.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolovat výjimky](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Návod: Určení místa, kde aplikace My. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
