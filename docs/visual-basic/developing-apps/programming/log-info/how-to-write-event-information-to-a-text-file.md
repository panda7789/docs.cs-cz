---
title: 'Postupy: Zápis informací o události do textového souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352076"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Postupy: Zápis informací o události do textového souboru (Visual Basic)

Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, `My.Application.Log.WriteEntry` jak pomocí metody protokolovat trasování informací do souboru protokolu.

### <a name="to-add-and-configure-the-file-log-listener"></a>Přidání a konfigurace posluchače protokolu souborů

1. Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.

     \-nebo -

     Pokud není k dispozici žádný soubor app.config:

    1. V nabídce **Projekt** zvolte **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.

    3. Klikněte na **Přidat**.

2. Vyhledejte `<listeners>` oddíl v konfiguračním souboru aplikace.

     \<Posluchače> části najdete \<v části zdrojové> s atributem název "DefaultSource", který je vnořen v části \<system.diagnostics>, která je vnořena pod oddíl> konfigurace nejvyšší úrovně. \<

3. Přidejte tento `<listeners>` prvek do tohoto oddílu:

    ```xml
    <add name="FileLogListener" />
    ```

4. Vyhledejte `<sharedListeners>` oddíl `<system.diagnostics>` v části vnořený `<configuration>` pod oddíl nejvyšší úrovně.

5. Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Změňte hodnotu `customlocation` atributu do adresáře protokolu.

    > [!NOTE]
    > Chcete-li nastavit hodnotu vlastnosti listener, použijte atribut, který má stejný název jako vlastnost, se všemi písmeny v názvu malá písmena. Například `location` atributy `customlocation` a nastavují <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastností a.

### <a name="to-write-event-information-to-the-file-log"></a>Zápis informací o událostech do protokolu souborů

Pomocí `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` or zapište informace do protokolu souborů. Další informace naleznete v [tématu How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po konfiguraci naslouchací proces protokolu souboru pro sestavení obdrží všechny zprávy, které `My.Application.Log` píše z tohoto sestavení.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
