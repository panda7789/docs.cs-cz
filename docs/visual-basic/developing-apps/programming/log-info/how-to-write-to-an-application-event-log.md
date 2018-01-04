---
title: "Postupy: Zápis do protokolu událostí aplikace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8225deaac92b4f375f57501875e13216b35a120d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a>Postupy: Zápis do protokolu událostí aplikace (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty při zápisu informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje postup konfigurace naslouchací proces protokolu událostí, takže `My.Application.Log` informace trasování zapíše do protokolu událostí aplikace.  
  
 Nelze zapisovat do protokolu zabezpečení. Aby bylo možné zapsat do systémového protokolu, musí být členem skupiny účet LocalSystem nebo správce.  
  
 Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**. Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).  
  
> [!NOTE]
>  Protokoly událostí nejsou podporovány v systému Windows 95, Windows 98 nebo Windows Millennium Edition.  
  
### <a name="to-add-and-configure-the-event-log-listener"></a>Přidání a konfigurace naslouchací proces protokolu událostí  
  
1.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.  
  
     \-nebo –  
  
     Pokud není dostupný žádný soubor app.config,  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.  
  
    3.  Klikněte na tlačítko **přidat**.  
  
2.  Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.  
  
     Zjistíte, `<listeners>` kapitoly `<source>` části s názvem atributu "DefaultSource", která je vnořená `<system.diagnostics>` oddíl, což je vnořená do nejvyšší úrovně `<configuration>` části.  
  
3.  Přidejte tento element do `<listeners>` části:  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
5.  Přidejte tento element do `<sharedListeners>` části:  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     Nahraďte `APPLICATION_NAME` s názvem vaší aplikace.  
  
    > [!NOTE]
    >  Aplikace obvykle zaznamená pouze chyby do protokolu událostí. Informace o filtrování výstupu protokolu najdete v tématu [návod: filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
### <a name="to-write-event-information-to-the-event-log"></a>Zápis informací o události do protokolu událostí  
  
-   Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do protokolu událostí. Další informace najdete v tématu [postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po dokončení konfigurace naslouchací proces protokolu událostí pro sestavení, obdrží všechny zprávy, která `My.Applcation.Log` zapíše z tohoto sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
