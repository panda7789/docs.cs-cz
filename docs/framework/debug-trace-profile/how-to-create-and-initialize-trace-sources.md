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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 805e1cc7d1def74a2a3e7b28afd052be1c4836c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596838"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Postupy: Vytváření a inicializace zdrojů trasování
<xref:System.Diagnostics.TraceSource> Třídu aplikace používá k vytvoření trasování, které lze asociovat s aplikací. <xref:System.Diagnostics.TraceSource> poskytuje metody trasování, které vám umožní snadno trasovat události, trasovat data a vydávat informační trasování. Trasování výstupu z <xref:System.Diagnostics.TraceSource> může být vytvořeno a inicializováno s nebo bez použití konfiguračních souborů. Toto téma obsahuje pokyny pro obě možnosti. Doporučujeme však použít konfigurační soubory pro usnadnění opětovné konfigurace trasování vyprodukované zdroji trasování za běhu.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Vytvoření a Inicializace zdroje trasování pomocí konfiguračního souboru  
  
1. Vytvořte projekt konzolové aplikace Visual Studio a nahraďte zadaný kód následujícím kódem. Tento kód protokoluje chyby a upozornění a vypíše některé z nich do konzoly a některé z nich do souboru myListener, který je vytvořen pomocí položek v konfiguračním souboru.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Přidání konfiguračního souboru aplikace, pokud jeden není uveden do projektu pro inicializaci zdroje trasování s názvem `TraceSourceApp` v příkladu kódu v kroku 1.  
  
3. Nahraďte výchozí obsah souboru konfigurace následujícím nastavením pro inicializaci naslouchacího procesu trasování konzoly a naslouchacího procesu text zapisovač trasování pro zdroj trasování, který byl vytvořen v kroku 1.  
  
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
  
     Kromě konfigurace posluchačů trasování, konfigurační soubor vytvoří filtry pro oba posluchače a vytvoří zdroj přepínače pro zdroj trasování. Pro přidávání posluchačů trasování jsou uvedeny dvě metody: Přidání posluchače přímo ke zdroji trasování a přidání posluchače do sdílené kolekce posluchačů a následné přidání podle názvu do zdroje trasování. Filtry identifikované pro dva naslouchací procesy jsou inicializovány s jinými zdrojovými úrovněmi. Výsledkem je některé zprávy jsou zapisovány pouze jedním ze dvou posluchačů.  
  
     Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy je aplikace inicializována. Aplikace můžete dynamicky měnit vlastnosti nastavením konfiguračního souboru pro přepsání jakéhokoli nastavení zadaného uživatelem. Můžete například chtít zajistit, aby kritické zprávy byly odesílány vždy do textového souboru, bez ohledu na aktuální nastavení konfigurace. Příklad kódu ukazuje, jak přepsat nastavení konfiguračního souboru k zajištění, aby kritické zprávy se zobrazují pro posluchače trasování.  
  
     Změna nastavení konfiguračních souborů při provádění aplikace nezmění výchozí nastavení. Chcete-li změnit nastavení, musíte restartovat aplikaci nebo programově aktualizovat aplikace pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Inicializace zdrojů trasování, posluchačů a filtrů bez konfiguračního souboru  
  
- Použijte následující příklad kódu povolíte trasování prostřednictvím zdroje trasování bez použití konfiguračního souboru. Toto není doporučený postup, ale mohou nastat okolnosti, ve kterých nechcete záviset na konfiguračních souborech k zajištění sledování.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
