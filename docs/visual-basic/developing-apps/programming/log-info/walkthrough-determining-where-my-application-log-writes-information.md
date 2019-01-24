---
title: Určení, kam objekt My.Application.Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: bafb307eff6a5ce6fd6dff823abe2f68b7725f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662670"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>Průvodce: Určení, kam objekt My.Application.Log zapisuje informace (Visual Basic)
`My.Application.Log` Objektu lze zapsat informace na několik součástí naslouchajících protokolům. Součásti naslouchající protokolům jsou nakonfigurované pomocí konfiguračního souboru počítače a lze přepsat pomocí konfiguračního souboru aplikace. Toto téma popisuje výchozí nastavení a jak určit nastavení pro vaši aplikaci.  
  
 Další informace o výchozích umístění výstupu najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>Chcete-li zjistit naslouchacích procesů pro My.Application.Log  
  
1.  Vyhledejte sestavení konfiguračního souboru. Pokud vyvíjíte sestavení, můžete přístup k souboru app.config v sadě Visual Studio z **Průzkumníka řešení**. V opačném případě je název konfiguračního souboru sestavení název s ".config" a je umístěn ve stejném adresáři jako sestavení.  
  
    > [!NOTE]
    >  Ne všechna sestavení měla v konfiguračním souboru.  
  
     Konfigurační soubor je soubor XML.  
  
2.  Vyhledejte `<listeners>` sekci `<source>` části s `name` atribut "DefaultSource" v `<sources>` oddílu. `<sources>` Je umístěna v `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
     Pokud tyto části neexistují, je nakonfigurovat konfiguračního souboru počítače `My.Application.Log` protokolu naslouchacích procesů. Následující kroky popisují, jak zjistit, co definuje konfigurační soubor počítače:  
  
    1.  Vyhledejte soubor počítače machine.config. Obvykle se nachází v *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* adresáře, kde `SystemRoot` je adresář operačního systému a `frameworkVersion` je verze [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Nastavení v souboru machine.config lze přepsat pomocí konfiguračního souboru aplikace.  
  
         Pokud neexistuje volitelné prvky uvedené níže, můžete je vytvořit.  
  
    2.  Vyhledejte `<listeners>` sekci `<source>` části s `name` atribut "DefaultSource", `<sources>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
         Pokud tyto části neexistují, pak bude `My.Application.Log` má pouze výchozí posluchače protokolu.  
  
3.  Vyhledejte <`add>` prvky <`listeners>` oddílu.  
  
     Tyto prvky přidat naslouchacích procesů s názvem protokolu k `My.Application.Log` zdroje.  
  
4.  Vyhledejte `<add>` prvků s názvy součásti naslouchající protokolům v `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.  
  
5.  Data inicializace naslouchacího procesu pro mnoho typů sdílené moduly pro naslouchání, obsahuje popis kde naslouchací proces nasměruje data:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchacího procesu zapisuje do souboru protokolu, jak je popsáno v úvodu.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchacího procesu zapisuje informace do protokolu událostí počítače určené `initializeData` parametru. Chcete-li zobrazit protokol událostí, můžete použít **Průzkumníka serveru** nebo **Prohlížeč událostí Windows**. Další informace najdete v tématu [události trasování událostí pro Windows v rozhraní .NET Framework](../../../../framework/performance/etw-events.md).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> naslouchacích procesů zapisovat do souboru zadaného v `initializeData` parametru.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchacího procesu zapisuje do konzoly příkazového řádku.  
  
    -   Informace o tom, kde psát jiných typů součástí naslouchajících protokolům informace najdete v dokumentaci tohoto typu.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Postupy: Zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [Návod: Změna, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Trasování událostí pro Windows – události v rozhraní .NET Framework](../../../../framework/performance/etw-events.md)
- [Řešení potíží: Součásti naslouchající protokolům](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
