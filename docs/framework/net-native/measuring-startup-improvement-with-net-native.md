---
title: "Měření zlepšení spuštění pomocí .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2486aa4daa5682f09b9cd5da8eac4b9071671a3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="measuring-startup-improvement-with-net-native"></a>Měření zlepšení spuštění pomocí .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)]výrazně zlepší doba spuštění aplikace. Tomuto vylepšení je zvláště patrné na přenosné zařízení úsporný a s komplexní aplikace. Toto téma vám pomůže začít pracovat s základní instrumentace potřebné k měření tomuto vylepšení spuštění.  
  
 Usnadňujících vyšetřování výkonu rozhraní .NET Framework a Windows pomocí představuje rozhraní události trasování událostí pro Windows (ETW), umožňuje aplikaci, kterou chcete upozornit, když dojde k událostem tooling volat. Potom můžete nástroj nazvaný nástroje PerfView můžete snadno zobrazit a analyzovat události trasování událostí pro Windows. Toto téma vysvětluje, jak:  
  
-   Použití <xref:System.Diagnostics.Tracing.EventSource> třídy pro vydávání událostí.  
  
-   Pomocí nástroje PerfView shromažďovat události.  
  
-   Pokud chcete zobrazit tyto události pomocí nástroje PerfView.  
  
## <a name="using-eventsource-to-emit-events"></a>Pomocí EventSource pro vydávání událostí  
 <xref:System.Diagnostics.Tracing.EventSource>poskytuje základní třídu, ze které chcete vytvořit vlastního zprostředkovatele událostí. Obecně platí, že vytvořit podtřídou třídy <xref:System.Diagnostics.Tracing.EventSource> a zabalení `Write*` metody s vlastními metody události. Vzor singleton se obecně používají pro každou <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Například v následujícím příkladu třída slouží k měření dvě vlastnosti výkonu:  
  
-   Čas, dokud `App` konstruktoru třídy byla volána.  
  
-   Čas, dokud `MainPage` konstruktor byla volána.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Můžete si zde všimnout několik věci. Nejprve je typu singleton vytvořen v `AppEventSource.Log`. Tato instance se použije pro všechny protokolování. Druhý, každá z metod událostí má <xref:System.Diagnostics.Tracing.EventAttribute>. To pomáhá nástrojů přidružit index <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metoda s metodu, která byla volána na `AppEventSource`.  
  
 Všimněte si, že tyto události jsou čistě ilustrativní. Většinu kódu aplikace se spustí po tyto události. Měli byste se seznámit události, které v kódu odpovídají interakcí, ty měřit a zlepšit těchto srovnávacích testů. Navíc sami události protokolu pouze jedna instance v čase. Často je užitečné mít spárovat, spuštění a zastavení události pro všechny operace. Při zkoumání aplikace spuštění, spuštění událost je obecně událostí "Proces/Start", který vysílá operační systém.  
  
 Předpokládejme například, že vytváříte čtečku RSS. Několik zajímavé umístění do protokolu událostí se:  
  
-   Při prvním zobrazení hlavní stránky.  
  
-   Když jsou staré scénářů RSS deserializovat z místního úložiště.  
  
-   Když aplikace začne synchronizuje nové scénáře.  
  
-   Když aplikace dokončil synchronizuje nové scénáře.  
  
 Instrumentaci aplikace je jednoduchý: stačí zavolat odpovídající metodu v odvozené třídě. Pomocí `AppEventSource` z předchozího příkladu, můžete instrumentovat aplikace takto:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Pokud aplikace není instrumentována, jste připravení shromažďovat události.  
  
## <a name="gathering-events-with-perfview"></a>Shromažďování událostí pomocí nástroje PerfView  
 Nástroje PerfView používá události trasování událostí pro pomoc nejrůznějším vyšetřování výkonu ve vaší aplikaci. Zahrnuje také konfiguraci s grafickým uživatelským rozhraním, které vám umožní zapnout protokolování pro různé typy událostí, nebo vypnout. Nástroje PerfView je bezplatný nástroj a si můžete stáhnout z [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=28567). Další informace, podívejte se [kurz videa nástroje PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  Nástroje PerfView nelze použít ke shromažďování událostí v systémech ARM. Shromažďování událostí v systémech ARM, použijte zapisovač požadavku výkonu webové systému Windows (části). Další informace najdete v tématu [hovou Morrison příspěvku na blogu](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Můžete také vyvolat nástroje PerfView z příkazového řádku. Do protokolu pouze události od poskytovatele, otevřete okno příkazového řádku a zadejte příkaz:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 kde:  
  
 `-KernelEvents:Process`  
 Označuje, že chcete vědět, když proces spustí a zastaví. Událost procesu a spustit musíte pro vaši aplikaci, můžete bude odečítat od jiných událostí časy.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Vypne jiných poskytovatelů, které nástroje PerfView zapne ve výchozím nastavení a změní na poskytovateli Moje_firma-Moje aplikace.  (Hvězdička označuje, že se jedná <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Označuje, že chcete spustit shromažďování a uložit data do outputFile.etl.zip.  
  
 Po spuštění nástroje PerfView spuštění aplikace. Existuje několik postupů k mějte na paměti při spuštění aplikace:  
  
-   Použití sestavení pro vydání, není sestavení ladicí verze. Sestavení pro ladění často obsahují další chyby kontroly a kód, který může způsobit, že aplikaci, kterou chcete spustit něco pomalejší, než se očekávalo pro zpracování chyb.  
  
-   Používající vaši aplikaci s připojit ladicí program, ovlivňuje výkon vaší aplikace.  
  
-   Windows používá několik strategií ukládání do mezipaměti pro urychlení časy spuštění aplikace. Pokud vaše aplikace je aktuálně uložené do mezipaměti v paměti a nemá být načtená z disku, spustí rychleji. K zajištění konzistence, spusťte a zavřete aplikaci několikrát před jeho měření.  
  
 Pokud jste spuštění aplikace, tak, aby nástroje PerfView může shromažďovat emitovaného události, vyberte **zastavit kolekce** tlačítko. Obecně platí by se měla zastavit kolekce před jeho zavřením vaší aplikace, takže neobdržíte nadbytečné události. Pokud jste měření výkonu vypnutí nebo pozastavení, budete ale chcete pokračovat kolekce.  
  
## <a name="displaying-the-events"></a>Zobrazení událostí  
 K zobrazení událostí, která již byla vybrána, otevřete .etl pomocí nástroje PerfView nebo. etl.zip souboru, kterou jste vytvořili a zvolte **události**. Trasování událostí pro Windows se mají shromažďovat informace o velké množství událostí, včetně událostí z jiných procesů. Umožňuje zaměřit se šetření, proveďte následující textová pole v zobrazení události:  
  
-   V **proces filtru** zadejte název vaší aplikace (bez ".exe").  
  
-   V **filtr typy událostí** zadejte `Process/Start | MyCompany-MyApp`. Toto nastaví filtr pro události z Moje_firma-Moje aplikace a událostí systému Windows jádra a proces nebo spustit.  
  
 Všechny události uvedené v levém podokně vyberte (Ctrl + A) a vyberte **Enter** klíč. Nyní byste měli vidět časová razítka z jednotlivých událostí. Tato časová razítka se vztahují k zahájení trasování, takže budete muset odečtena čas jednotlivých událostí z čas zahájení procesu k identifikaci uplynulý čas od spuštění. Pokud používáte kombinaci kláves Ctrl + kliknutí vybrat dvě časová razítka, se zobrazí rozdíl mezi zobrazovat ve stavovém řádku v dolní části stránky. Díky tomu budete moci prohlédnout uplynulý čas mezi všechny dvě události v zobrazení (včetně procesu spuštění). Můžete otevřít na místní nabídku pro zobrazení a vybrat z mnoha možností užitečné, jako je export do souborů CSV nebo otevřít aplikaci Microsoft Excel uložit nebo zpracování dat.  
  
 Zopakováním postupu pro původní aplikace a verze, který jste vytvořili pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězec, můžete porovnat rozdíl ve výkonu.   [!INCLUDE[net_native](../../../includes/net-native-md.md)]aplikace obecně spustit rychleji než jinou hodnotu než[!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace. Pokud vás zajímají podrobnější tápat nástroje PerfView můžete také poznat části kódu, které trvá nejvíce času. Další informace, podívejte se [nástroje PerfView kurzy](http://channel9.msdn.com/Series/PerfView-Tutorial) nebo si můžete přečíst [položku blogu hovou Morrison](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Tracing.EventSource>
