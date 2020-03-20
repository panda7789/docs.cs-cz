---
title: 'Postupy: Vytváření a inicializace zdrojů trasování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174729"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Postupy: Vytváření a inicializace zdrojů trasování
Třída <xref:System.Diagnostics.TraceSource> se používá aplikace k výrobě trasování, které mohou být přidruženy k aplikaci. <xref:System.Diagnostics.TraceSource>Poskytuje metody trasování, které umožňují snadno sledovat události, trasování dat a vydávat informační trasování. Výstup trasování z <xref:System.Diagnostics.TraceSource> lze vytvořit a inicializovat s nebo bez použití konfiguračních souborů. Toto téma obsahuje pokyny pro obě možnosti. Doporučujeme však použít konfigurační soubory k usnadnění rekonfigurace trasování produkovaných zdroji trasování za běhu.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Vytvoření a inicializaci zdroje trasování pomocí konfiguračního souboru  
  
1. Vytvořte projekt aplikace konzoly Visual Studio (.NET Framework) a nahraďte dodaný kód následujícím kódem. Tento kód protokoluje chyby a upozornění a výstupy některé z nich do konzoly a některé z nich do souboru myListener, který je vytvořen položky v konfiguračním souboru.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Přidejte konfigurační soubor aplikace, pokud není k dispozici, do `TraceSourceApp` projektu inicializovat zdroj trasování pojmenovaný v příkladu kódu v kroku 1.  
  
3. Nahraďte výchozí obsah konfiguračního souboru následujícími nastaveními pro inicializaci posluchače trasování konzoly a posluchače trasování zapisovače textu pro zdroj trasování, který byl vytvořen v kroku 1.  
  
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
  
     Kromě konfigurace posluchačů trasování konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování. Dvě techniky jsou zobrazeny pro přidání naslouchací procesy trasování: přidání posluchače přímo do zdroje trasování a přidání posluchače do sdílené posluchače kolekce a potom jej přidat podle názvu do zdroje trasování. Filtry určené pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi. To má za následek některé zprávy zapisovány pouze jeden ze dvou posluchačů.  
  
     Konfigurační soubor inicializuje nastavení zdroje trasování v době, kdy je aplikace inicializována. Aplikace může dynamicky změnit vlastnosti nastavené konfiguračním souborem tak, aby přepsaly všechna nastavení určená uživatelem. Můžete například chtít zajistit, aby kritické zprávy byly vždy odesílány do textového souboru bez ohledu na aktuální nastavení konfigurace. Ukázkový kód ukazuje, jak přepsat nastavení konfiguračního souboru, aby bylo zajištěno, že kritické zprávy jsou výstupem na posluchače trasování.  
  
     Změna nastavení konfiguračního souboru při provádění aplikace nezmění počáteční nastavení. Chcete-li změnit nastavení, musíte aplikaci restartovat nebo programově <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> aktualizovat aplikaci pomocí metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Inicializaci zdrojů trasování, naslouchacích procesů a filtrů bez konfiguračního souboru  
  
- Pomocí následujícího ukázkového kódu povolte trasování přes zdroj trasování bez použití konfiguračního souboru. Toto není doporučený postup, ale mohou nastaly okolnosti, za kterých nechcete být závislí na konfiguračních souborech, abyste zajistili trasování.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
