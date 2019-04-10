---
title: 'Postupy: Zápis informací o události do textového souboru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: e696ccb7327197c2f3a2468d30085dc6d390e034
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312709"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Postupy: Zápis informací o události do textového souboru (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci. Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda ukládá do protokolu trasování údaje do souboru protokolu.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Přidání a konfigurace naslouchacího procesu protokolu souborů  
  
1. Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.  
  
     \- nebo –  
  
     Pokud není dostupný žádný soubor app.config:  
  
    1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
    2.  Z **přidat novou položku** dialogového okna zvolte **konfiguračního souboru aplikace**.  
  
    3.  Klikněte na **Přidat**.  
  
2. Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.  
  
     Vás bude \<naslouchacích procesů > v tématu \<zdroj > část s atributem name "DefaultSource", která je vnořená v rámci \<system.diagnostics > oddíl, což je vnořený nejvyšší úrovně \<konfigurace > oddílu.  
  
3. Přidejte tento element, který `<listeners>` části:  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. Vyhledejte `<sharedListeners>` tématu `<system.diagnostics>` části, v nejvyšší úrovni `<configuration>` oddílu.  
  
5. Přidejte tento element, který `<sharedListeners>` části:  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Změňte hodnotu `customlocation` atribut k adresáři protokolů.  
  
    > [!NOTE]
    >  Pokud chcete nastavit hodnotu vlastnosti naslouchacího procesu, použijte atribut, který má stejný název jako vlastnost, kde jsou všechna písmena v názvu malá. Například `location` a `customlocation` atributy nastavte hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastnosti.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Zápis informací o události do souboru protokolu  
  
-   Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do souboru protokolu. Další informace najdete v tématu [jak: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [jak: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Po dokončení konfigurace naslouchacího procesu protokolu souborů pro sestavení přijímá všechny zprávy, které `My.Application.Log` zapíše z tohoto sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
