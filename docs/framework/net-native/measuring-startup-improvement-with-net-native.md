---
title: Měření zlepšení spuštění pomocí .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2603c29fe9108a32f3c3ba86a5aba9fae5042b17
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025516"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Měření zlepšení spuštění pomocí .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] výrazně zlepšuje dobu spuštění aplikace. Toto vylepšení je patrné v na přenosných a s nízkou spotřebou zařízení a s komplexní aplikace. Toto téma vám pomůže začít pracovat s základní instrumentací potřebné k měření zlepšení toto spuštění.  
  
 Pro usnadnění vyšetřování výkonu, rozhraní .NET Framework a Windows pomocí rozhraní události trasování událostí pro Windows (ETW), která vaše aplikace bude informovat, nástrojů, když dojde k událostem volat. Potom můžete nástroj zvaný PerfView můžete snadno zobrazit a analyzovat událostí trasování událostí pro Windows. Toto téma vysvětluje, jak:  
  
-   Použití <xref:System.Diagnostics.Tracing.EventSource> třídy vysílat události.  
  
-   Pomocí nástroje PerfView shromažďovat události.  
  
-   Pokud chcete zobrazit tyto události pomocí nástroje PerfView.  
  
## <a name="using-eventsource-to-emit-events"></a>Generování událostí pomocí EventSource  
 <xref:System.Diagnostics.Tracing.EventSource> poskytuje základní třídu, ze kterého se má vytvořit vlastního zprostředkovatele událostí. Obecně platí, vytvořit podtřídu <xref:System.Diagnostics.Tracing.EventSource> a zalomení `Write*` metody s vašimi vlastními metodami události. Vzor s jedním prvkem se obecně používají pro každou <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Například třída v následujícím příkladu můžete použít k měření dvě výkonové charakteristiky:  
  
-   Čas do `App` byla volána konstruktor třídy.  
  
-   Čas do `MainPage` byla volána konstruktor.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Všimněte si některé věci. Nejprve se vytvoří jednotlivý prvek v `AppEventSource.Log`. Tato instance se použije pro všechny protokolování. Za druhé, má každá metoda událostí <xref:System.Diagnostics.Tracing.EventAttribute>. To pomáhá nástroje přidružit index <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody s metodou, která byla volána pro `AppEventSource`.  
  
 Všimněte si, že tyto události jsou čistě příkladů. Většinu kódu aplikace se spustí po těchto událostí. Měli byste porozumět události v kódu odpovídají interakce uživatelů, měřit ty a zlepšit těchto srovnávací testy. Také samotné události protokolu jenom jednu instanci v čase. Často je užitečné mít spárované spuštění a zastavení událostí pro všechny operace. Při zkoumání spuštění aplikace, je událost zahájení obecně událost "Proces/Start", který vysílá operační systém.  
  
 Předpokládejme například, že vytváříte čtečku RSS. Pár zajímavých míst do protokolu událostí je:  
  
-   Když hlavní nejprve vykreslením stránky.  
  
-   Když jsou staré RSS scénáře deserializovat z místního úložiště.  
  
-   Vaše aplikace zahájení synchronizace nových příběhů.  
  
-   Vaše aplikace má po dokončení synchronizace nových příběhů.  
  
 Instrumentace aplikace je jednoduché: stačí zavolat vhodnou metodu v odvozené třídě. Pomocí `AppEventSource` z předchozího příkladu, vám umožňuje instrumentovat aplikaci následujícím způsobem:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Když je aplikace instrumentována, budete připraveni ke shromažďování událostí.  
  
## <a name="gathering-events-with-perfview"></a>Shromažďování událostí pomocí nástroje PerfView  
 PerfView používá trasování událostí pro Windows můžete provádět nejrůznější vyšetřování výkonu v aplikaci. Obsahuje také konfiguraci grafického uživatelského rozhraní, který umožňuje vypnutí nebo zapnutí protokolování pro různé typy událostí. Je bezplatný nástroj PerfView a si můžete stáhnout z [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567). Další informace, podívejte se [výukových videí PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  PerfView nelze použít ke shromažďování událostí pro systémy ARM. Shromažďování událostí v systémech ARM, pomocí požadavku webové Windows Performance Recorder (části). Další informace najdete v tématu [daňové Morrison blogový příspěvek](https://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Můžete také vyvolat PerfView z příkazového řádku. Pro přihlášení jenom události od poskytovatele, otevřete okno příkazového řádku a zadejte příkaz:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 kde:  
  
 `-KernelEvents:Process`  
 Označuje, že chcete vědět, kdy proces spouští a zastavuje. Události spuštění procesu/potřebujete pro vaši aplikaci, může být odečtena od jindy události.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Vypne jiných poskytovatelů služeb, které PerfView zapne ve výchozím nastavení a zapne poskytovateli společnost MyApp.  (Hvězdička znamená, že se jedná <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Označuje, že chcete spustit shromažďování dat a jejich ukládání do outputFile.etl.zip.  
  
 Po spuštění nástroje PerfView spuštění aplikace. Mějte na paměti při spuštění aplikace některé věci:  
  
-   Použijte sestavení pro vydání, ne sestavení pro ladění. Sestavení pro ladění často obsahují další chyby kontroly a kód, který může způsobit, že vaše aplikace poběží pomaleji, než se očekávalo pro zpracování chyb.  
  
-   Vaše aplikace běžela s připojen jiný ladicí program má vliv na výkon vaší aplikace.  
  
-   Windows používá několik strategií, které ukládání do mezipaměti pro urychlení doby spuštění aplikace. Pokud vaše aplikace je aktuálně uloženo do mezipaměti v paměti a nemusí být načteny z disku, spustí rychleji. K zajištění konzistence, spusťte a zavřete vaši aplikaci před měřili několikrát.  
  
 Pokud jste spustíte svou aplikaci tak, aby PerfView může shromažďovat události emitovaný, zvolte **zastavit shromažďování** tlačítko. Obecně byste navíc měli zastavit shromažďování před jeho zavřením vaší aplikace, aby se vám nadbytečné události. Pokud jste měření výkonu vypnutí nebo pozastavení účtu, budete však chcete pokračovat kolekce.  
  
## <a name="displaying-the-events"></a>Zobrazení událostí  
 Chcete-li zobrazit události, které již byla shromážděna, otevřete .etl pomocí nástroje PerfView nebo. etl.zip vytvořeného souboru a zvolte **události**. Trasování událostí pro Windows se mají shromažďovat informace o velký počet událostí, včetně událostí z jiných procesů. Pokud chcete zaměřit svůj výzkum, proveďte následující textová pole v zobrazení události:  
  
-   V **filtr procesu** zadejte název vaší aplikace (bez ".exe").  
  
-   V **filtr typů událostí** zadejte `Process/Start | MyCompany-MyApp`. Tím se nastaví filtr pro události z události Windows jádra / / spuštění procesu a společnost MyApp.  
  
 Všechny události uvedené v levém podokně vyberte (Ctrl-A) a zvolte **Enter** klíč. Teď byste měli vidět časová razítka každé události. Tato časová razítka jsou relativní vzhledem k zahájení trasování, takže budete mít odečíst času každé události z času začátku procesu k identifikaci uplynulý čas od spuštění. Pokud použijete Ctrl + kliknutí pro výběr dva časová razítka, uvidíte rozdíl mezi nimi zobrazí ve stavovém řádku v dolní části stránky. To usnadňuje zobrazte uplynulý čas mezi jakékoli dvě události v zobrazení (včetně spuštění procesu). Můžete otevřít místní nabídku pro zobrazení a vybrat z řady užitečné možnosti, jako je export do souborů CSV nebo otevřete aplikaci Microsoft Excel k uložení nebo zpracování dat.  
  
 Zopakováním postupu pro původní aplikace a verze, který jste vytvořili pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězec, můžete porovnat rozdíl ve výkonu.   [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace obvykle je dobré začít rychleji než jinou hodnotu než[!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace. Pokud vás zajímají podrobnější si PerfView můžete také určit části kódu, které trvá nejdéle. Další informace, podívejte se [PerfView kurzy](http://channel9.msdn.com/Series/PerfView-Tutorial) nebo si přečtěte [daňové Morrison blogu](https://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Tracing.EventSource>
