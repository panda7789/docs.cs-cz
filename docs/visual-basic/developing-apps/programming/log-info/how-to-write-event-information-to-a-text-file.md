---
title: 'Postupy: Zápis informací o události do textového souboru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 4a34b57eb0a22dcf206456775cdd5817431292e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956827"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Postupy: Zápis informací o události do textového souboru (Visual Basic)
Pomocí `My.Application.Log` objektů a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak použít `My.Application.Log.WriteEntry` metodu k protokolování informací o trasování do souboru protokolu.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu souborů  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.  
  
     \- nebo –  
  
     Pokud neexistuje žádný soubor App. config:  
  
    1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.  
  
    2. V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.  
  
    3. Klikněte na **Přidat**.  
  
2. `<listeners>` Vyhledejte část v konfiguračním souboru aplikace.  
  
     Oddíl \<Listeners > \<v oddílu Source > najdete v části s názvem "DefaultSource", \<která je vnořená do oddílu System. Diagnostics >, která je vnořená do nejvyšší úrovně. \<oddíl > Konfigurace  
  
3. Přidejte tento element do této `<listeners>` části:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Vyhledejte část v oddílu, která je vnořená pod oddíl nejvyšší úrovně `<configuration>`. `<system.diagnostics>` `<sharedListeners>`  
  
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
    > Chcete-li nastavit hodnotu vlastnosti naslouchacího procesu, použijte atribut, který má stejný název jako vlastnost, přičemž všechna písmena v názvu jsou malá. Například `location` atributy a `customlocation` nastavují<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> hodnoty vlastností a.<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A>  
  
### <a name="to-write-event-information-to-the-file-log"></a>Zápis informací o události do protokolu souborů  
  
- Pomocí metody `My.Application.Log.WriteException` nebo zapište informace do protokolu souborů. `My.Application.Log.WriteEntry` Další informace najdete v tématu [jak: Pište zprávy](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) protokolu a [postupy: Protokoluje](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)výjimky.  
  
     Po nakonfigurování naslouchacího procesu protokolu souborů pro sestavení obdrží všechny zprávy, které `My.Application.Log` se zapisují z tohoto sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolovat výjimky](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
