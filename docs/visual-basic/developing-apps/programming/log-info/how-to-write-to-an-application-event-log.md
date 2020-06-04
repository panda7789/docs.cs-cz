---
title: 'Postupy: Zápis do protokolu událostí aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410033"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)

Pomocí `My.Application.Log` objektů a můžete `My.Log` zapisovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak nakonfigurovat naslouchací proces protokolu událostí, který `My.Application.Log` zapisuje trasovací informace do protokolu událostí aplikace.

Do protokolu zabezpečení nelze zapisovat. Aby bylo možné zapisovat do systémového protokolu, musíte být členem účtu LocalSystem nebo správce.

Chcete-li zobrazit protokol událostí, můžete použít **Průzkumník serveru** nebo **Windows Prohlížeč událostí**. Další informace najdete v tématu [události ETW v .NET Framework](../../../../framework/performance/etw-events.md).

## <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu událostí

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

    \-ani

    Pokud soubor App. config neexistuje,

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Add** (Přidat).

2. Vyhledejte `<listeners>` část v konfiguračním souboru aplikace.

    `<listeners>`Část v `<source>` oddílu najdete s názvem atribut "DefaultSource", který je vnořen do `<system.diagnostics>` oddílu, který je vnořen v části nejvyšší úrovně `<configuration>` .

3. Přidejte tento element do této `<listeners>` části:

    ```xml
    <add name="EventLog"/>
    ```

4. Vyhledejte část v části v `<sharedListeners>` `<system.diagnostics>` sekci nejvyšší úrovně `<configuration>` .

5. Přidejte tento element do této `<sharedListeners>` části:

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    Nahraďte `APPLICATION_NAME` názvem vaší aplikace.

    > [!NOTE]
    > Aplikace obvykle zapisuje pouze chyby do protokolu událostí. Informace o filtrování výstupu protokolu naleznete v tématu [Návod: filtrování výstupu my. Application. log](walkthrough-filtering-my-application-log-output.md).

## <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o události do protokolu událostí

Pomocí `My.Application.Log.WriteEntry` metody nebo `My.Application.Log.WriteException` zapište informace do protokolu událostí. Další informace naleznete v tématu [How to: Write log messages](how-to-write-log-messages.md) and [to: log Exceptions](how-to-log-exceptions.md).

Po nakonfigurování naslouchacího procesu protokolu událostí pro sestavení obdrží všechny zprávy, které `My.Application.Log` zapisují z tohoto sestavení.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](working-with-application-logs.md)
- [Postupy: Protokolování výjimek](how-to-log-exceptions.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](walkthrough-determining-where-my-application-log-writes-information.md)
