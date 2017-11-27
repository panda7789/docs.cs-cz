---
title: "Postupy: Vytváření a inicializace zdrojů trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1fc1e843bb5841fcd5571bb1b57d6fb449336240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Postupy: Vytváření a inicializace zdrojů trasování
<xref:System.Diagnostics.TraceSource> Třída se používá aplikace k vytvoření trasování, které může být spojeno s aplikací. <xref:System.Diagnostics.TraceSource>poskytuje metody trasování, které vám umožňují snadno události trasování, data trasování a problém informativní trasování. Výstup trasování <xref:System.Diagnostics.TraceSource> můžete vytvořit a inicializován s nebo bez použití konfiguračních souborů. Toto téma obsahuje pokyny pro obě možnosti. Doporučujeme však používají konfigurační soubory pro usnadnění Rekonfigurace trasování vyprodukované trasování zdrojů za běhu.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>K vytvoření a inicializace zdroj trasování pomocí konfiguračního souboru  
  
1.  Vytvoření projektu konzolové aplikace Visual Studio a zadaný kód nahraďte následujícím kódem. Tento kód protokoly chyb a varování a výstupy některé z nich ke konzole a některá z nich myListener soubor, který byl vytvořený položky v konfiguračním souboru.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  Přidání konfiguračního souboru aplikace, pokud není přítomný, do projektu se inicializovat zdroj trasování s názvem `TraceSourceApp` v příkladu v kroku 1.  
  
3.  Nahraďte obsah souboru výchozí konfiguraci následujících nastavení můžete inicializovat naslouchací proces trasování konzoly a naslouchací zapisovač textu pro trasování zdroj, který byl vytvořen v kroku 1.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Kromě konfigurace naslouchací procesy trasování, konfigurační soubor vytvoří filtry pro obě naslouchací procesy a vytvoří přepínač zdroje pro zdroj trasování. Pro přidání trasování – moduly naslouchání se zobrazují dvě techniky: Přidání naslouchací proces přímo na zdroj trasování a přidání naslouchací proces ke kolekci sdílené moduly pro naslouchání a následným přidáním podle názvu zdroje trasování. Filtry identifikovat pro dva naslouchací procesy jsou inicializovány s jinou zdrojovou úrovněmi. Výsledkem některé zprávy zapisovaný jenom jedna z dva naslouchací procesy.  
  
     Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy aplikace je inicializován. Aplikace můžete dynamicky měnit vlastnosti nastavit pomocí konfiguračního souboru pro přepsání nastavení zadaný uživatelem. Například můžete chtít zajistit kritické jsou vždy odesílání zpráv do textového souboru, bez ohledu na aktuální nastavení konfigurace. Příklad kódu ukazuje, jak k přepsání souboru nastavení konfigurace zajistit, že kritické zprávy se zobrazují naslouchací procesy trasování.  
  
     Změna souboru nastavení konfigurace, když spouští aplikaci počáteční nastavení nezmění. Chcete-li změnit nastavení, musíte aplikaci restartovat nebo prostřednictvím kódu programu obnovit aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metoda.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Inicializace zdrojů trasování, naslouchací procesy a filtry bez konfiguračního souboru  
  
-   Použijte následující příklad kódu povolení trasování prostřednictvím zdroj trasování bez použití konfiguračního souboru. Toto není doporučený postup, ale může být případech, ve kterých nechcete závisí na konfigurační soubory, aby trasování.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
