---
title: "Určení, kam objekt My.Application.Log zapisuje informace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4df7a80907b29a5eea79992f46c46603cbe2cc81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Návod: Zjištění, kam objekt My.Application.Log zapisuje informace (Visual Basic)
`My.Application.Log` Objekt může zapsat informace do několika naslouchací procesy pro protokoly. Naslouchací procesy pro protokoly jsou nakonfigurovány pomocí souboru konfigurace počítače a mohou být přepsány konfiguračním souboru aplikace. Toto téma popisuje výchozí nastavení a jak určit nastavení pro vaši aplikaci.  
  
 Další informace o výchozích umístění výstupu najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Chcete-li zjistit naslouchací procesy pro My.Application.Log  
  
1.  Vyhledejte soubor konfigurace je sestavení. Pokud vyvíjíte sestavení, můžete přístup k souboru app.config v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] z **Průzkumníku řešení**. Jinak název konfiguračního souboru je spolu s ".config" název sestavení a nachází se ve stejném adresáři jako sestavení.  
  
    > [!NOTE]
    >  Konfigurační soubor obsahuje Ne každé sestavení.  
  
     Konfigurační soubor je soubor XML.  
  
2.  Vyhledejte `<listeners>` v části `<source>` část s `name` atributu "DefaultSource", umístěný ve `<sources>` části. `<sources>` Je umístěna v `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
     Pokud tyto části nejsou k dispozici, pak může konfigurovat počítače konfigurační soubor `My.Application.Log` protokolu naslouchací procesy. Následující kroky popisují, jak zjistit, co definuje konfigurační soubor na počítači:  
  
    1.  Vyhledejte souboru machine.config. Obvykle se nachází v *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* adresáře, kde `SystemRoot` je adresář operačního systému a `frameworkVersion` je verze [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Konfigurační soubor aplikace je možné přepsat nastavení v souboru machine.config.  
  
         Pokud nejsou k dispozici níže uvedené volitelné prvky, můžete je vytvořit.  
  
    2.  Vyhledejte `<listeners>` v části `<source>` část s `name` atribut "DefaultSource", `<sources>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
         Pokud tyto části nejsou k dispozici, pak se `My.Application.Log` má pouze výchozí posluchače protokolu.  
  
3.  Vyhledejte <`add>` elementů v <`listeners>` části.  
  
     Tyto prvky přidejte naslouchací procesy protokolu s názvem na `My.Application.Log` zdroje.  
  
4.  Vyhledejte `<add>` prvků s názvy součástí naslouchajících protokolům v `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.  
  
5.  Pro mnoho typů sdílené moduly pro naslouchání inicializační data obsahuje popis kde naslouchací proces nasměruje data:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do protokolového souboru, jak je popsáno v zavedení.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje informace do protokolu událostí počítače určeného `initializeData` parametr. Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí systému Windows**. Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisují do souboru určeném v `initializeData` parametr.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces zapisuje do konzoly nástroje příkazového řádku.  
  
    -   Informace o kde jiné typy naslouchací procesy protokolu zapisují informace najdete v dokumentaci daného typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Postupy: protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [Události trasování událostí pro Windows v rozhraní .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)  
 [Řešení potíží: Součásti naslouchající protokolům](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
