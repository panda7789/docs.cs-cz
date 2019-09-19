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
ms.openlocfilehash: cab9cc33bd5a4697cac5de85de8aa72e7eb4d6c6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052705"
---
# <a name="how-to-create-and-initialize-trace-sources"></a>Postupy: Vytváření a inicializace zdrojů trasování
<xref:System.Diagnostics.TraceSource> Třída je používána aplikacemi k vytvoření trasování, která lze přidružit k aplikaci. <xref:System.Diagnostics.TraceSource>poskytuje metody trasování, které umožňují snadno sledovat události, trasovat data a vydávat informativní trasování. Výstup trasování z <xref:System.Diagnostics.TraceSource> lze vytvořit a inicializovat s nebo bez použití konfiguračních souborů. Toto téma poskytuje pokyny pro obě možnosti. Nicméně doporučujeme, abyste používali konfigurační soubory pro usnadnění rekonfigurace trasování, která jsou vytvářena pomocí zdrojů trasování v době běhu.  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>Vytvoření a inicializace zdroje trasování pomocí konfiguračního souboru  
  
1. Vytvořte projekt konzolové aplikace sady Visual Studio a nahraďte poskytnutý kód následujícím kódem. Tento kód protokoluje chyby a varování a výstupy některých z nich do konzoly a některé z nich jsou k souboru myListener, který je vytvořen položkami v konfiguračním souboru.  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. Přidejte konfigurační soubor aplikace (Pokud není k dispozici) do projektu pro inicializaci zdroje trasování s názvem `TraceSourceApp` v příkladu kódu v kroku 1.  
  
3. Nahraďte výchozí obsah konfiguračního souboru následujícím nastavením pro inicializaci naslouchacího procesu trasování konzoly a naslouchacího procesu trasování zapisovače textu pro zdroj trasování, který byl vytvořen v kroku 1.  
  
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
  
     Kromě konfigurace posluchačů trasování vytvoří konfigurační soubor filtry pro oba posluchače a vytvoří zdrojový přepínač pro zdroj trasování. Pro přidávání posluchačů trasování jsou zobrazeny dvě metody: Přidání naslouchacího procesu přímo do zdroje trasování a přidání naslouchacího procesu do sdílené kolekce posluchačů a jejich přidání podle názvu do zdroje trasování. Filtry identifikované pro dva naslouchací procesy jsou inicializovány s různými zdrojovými úrovněmi. Výsledkem je, že některé zprávy zapisují pouze jeden ze dvou posluchačů.  
  
     Konfigurační soubor inicializuje nastavení pro zdroj trasování v době, kdy byla aplikace inicializována. Aplikace může dynamicky měnit vlastnosti nastavené konfiguračním souborem pro přepsání všech nastavení zadaných uživatelem. Například můžete chtít zajistit, aby se kritické zprávy vždy odesílaly do textového souboru, bez ohledu na aktuální nastavení konfigurace. Vzorový kód ukazuje, jak přepsat nastavení konfiguračního souboru, aby bylo zajištěno, že kritické zprávy jsou výstupem posluchačů trasování.  
  
     Změna nastavení konfiguračního souboru během provádění aplikace nemění počáteční nastavení. Chcete-li změnit nastavení, musíte buď aplikaci restartovat, nebo programově aktualizovat aplikaci pomocí <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>Inicializace zdrojů trasování, posluchačů a filtrů bez konfiguračního souboru  
  
- Použijte následující vzorový kód pro povolení trasování prostřednictvím zdroje trasování bez použití konfiguračního souboru. Nejedná se o doporučený postup, ale může dojít ke situacím, kdy nechcete, aby se zajistilo trasování v konfiguračních souborech.  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
