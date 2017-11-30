---
title: "Postupy: Zápis informací o události do textového souboru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 944d874de5c3872f9efe5e287e5354c94c792b95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Postupy: Zápis informací o události do textového souboru (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace trasování do souboru protokolu.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>K přidání a konfiguraci naslouchacího procesu souboru protokolu  
  
1.  Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.  
  
     \-nebo –  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.  
  
    3.  Klikněte na tlačítko **přidat**.  
  
2.  Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.  
  
     Zjistíte, \<naslouchací procesy > tématu \<zdroje > části s názvem atributu "DefaultSource", která je vnořená \<system.diagnostics > oddíl, což je vnořená pod nejvyšší úrovně \<konfigurace > části.  
  
3.  Přidejte tento element do `<listeners>` části:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  Vyhledejte `<sharedListeners>` tématu `<system.diagnostics>` část, v nejvyšší úrovni `<configuration>` části.  
  
5.  Přidejte tento element do `<sharedListeners>` části:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Změňte hodnotu `customlocation` atribut adresář protokolu.  
  
    > [!NOTE]
    >  Pokud chcete nastavit hodnotu vlastnosti naslouchací proces, použijte atribut, který má stejný název jako vlastnost, kde jsou všechna písmena na malá písmena název. Například `location` a `customlocation` atributy nastavte hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastnosti.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Zápis informací o události do souboru protokolu  
  
-   Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do souboru protokolu. Další informace najdete v tématu [postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po dokončení konfigurace naslouchací proces protokolu souboru pro sestavení, obdrží všechny zprávy, která `My.Application.Log` zapíše z tohoto sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Postupy: protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
