---
title: 'Postupy: Zápis do protokolu událostí aplikace (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 78d7fbd7aa5cb0062a51145725a6fc2e9dce7525
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662631"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty při zápisu informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje, jak konfigurace naslouchacího procesu protokolu událostí tak `My.Application.Log` informace trasování zapíše do protokolu událostí aplikace.  
  
 Nelze zapisovat do protokolu zabezpečení. Aby bylo možné zapsat do systémového protokolu, musí být členem účtu LocalSystem nebo správce.  
  
 Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí Windows**. Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).  
  
> [!NOTE]
>  Protokoly událostí nepodporuje Windows 95, Windows 98 a Windows Millennium Edition.  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu událostí  
  
1.  Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.  
  
     \- nebo –  
  
     Pokud neexistuje žádný soubor app.config  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
    3.  Klikněte na **Přidat**.  
  
2.  Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.  
  
     Vás bude `<listeners>` tématu `<source>` část s atributem name "DefaultSource", která je vnořená v rámci `<system.diagnostics>` oddíl, což je vnořený na nejvyšší úrovni `<configuration>` části.  
  
3.  Přidejte tento element, který `<listeners>` části:  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
5.  Přidejte tento element, který `<sharedListeners>` části:  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Nahraďte `APPLICATION_NAME` s názvem vaší aplikace.  
  
    > [!NOTE]
    >  Aplikace obvykle zapisuje pouze chyby do protokolu událostí. Informace o filtrování výstupu protokolu najdete v tématu [názorný postup: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o události do protokolu událostí  
  
-   Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do protokolu událostí. Další informace najdete v tématu [jak: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [jak: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po dokončení konfigurace naslouchacího procesu protokolu událostí pro sestavení přijímá všechny zprávy, které `My.Applcation.Log` zapíše z tohoto sestavení.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Návod: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
