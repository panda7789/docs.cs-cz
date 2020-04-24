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

Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak použít `My.Application.Log.WriteEntry` metodu k protokolování informací o trasování do souboru protokolu.

### <a name="to-add-and-configure-the-file-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu souborů

1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.

     \-ani

     Pokud neexistuje žádný soubor App. config:

    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.

    3. Klikněte na tlačítko **Add** (Přidat).

2. Vyhledejte `<listeners>` část v konfiguračním souboru aplikace.

     Oddíl \<listeners> v oddílu \<source> najdete pomocí atributu name "DefaultSource", který je vnořen do oddílu \<System. Diagnostics>, který je vnořený pod oddílem> konfigurace nejvyšší úrovně. \<

3. Přidejte tento element do této `<listeners>` části:

    ```xml
    <add name="FileLogListener" />
    ```

4. Vyhledejte `<sharedListeners>` část v `<system.diagnostics>` oddílu, která je vnořená pod oddíl nejvyšší úrovně `<configuration>` .

5. Přidejte tento element do této `<sharedListeners>` části:

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     Změňte hodnotu `customlocation` atributu na adresář protokolu.

    > [!NOTE]
    > Chcete-li nastavit hodnotu vlastnosti naslouchacího procesu, použijte atribut, který má stejný název jako vlastnost, přičemž všechna písmena v názvu jsou malá. Například atributy `location` a `customlocation` nastavují hodnoty vlastností <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>

### <a name="to-write-event-information-to-the-file-log"></a>Zápis informací o události do protokolu souborů

Pomocí metody `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` zapište informace do protokolu souborů. Další informace naleznete v tématu [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

Po nakonfigurování naslouchacího procesu protokolu souborů pro sestavení obdrží všechny zprávy, které `My.Application.Log` se zapisují z tohoto sestavení.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
