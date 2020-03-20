---
title: Měření zlepšení spuštění pomocí .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
ms.openlocfilehash: 41a693f18ffea0e5ce0ca742bc251d147e8e3784
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181001"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Měření zlepšení spuštění pomocí .NET Native
.NET Native výrazně zlepšuje dobu spuštění aplikací. Toto zlepšení je patrné zejména na přenosných zařízeních s nízkým výkonem a u složitých aplikací. Toto téma vám pomůže začít se základní instrumentací potřebnou k měření tohoto vylepšení spuštění.  
  
 Pro usnadnění sledování výkonu rozhraní .NET Framework a Windows používají rozhraní pro sledování událostí pro Windows (ETW), které umožňuje vaší aplikaci upozorňovat nástroje, když dojde k událostem. Potom můžete použít nástroj s názvem PerfView snadno zobrazit a analyzovat události ETW. Toto téma vysvětluje, jak:  
  
- Pomocí <xref:System.Diagnostics.Tracing.EventSource> třídy vyzařovat události.  
  
- Použití PerfView shromažďovat tyto události.  
  
- Pomocí perfView zobrazíte tyto události.  
  
## <a name="using-eventsource-to-emit-events"></a>Použití zdroje událostí k vyzařování událostí  
 <xref:System.Diagnostics.Tracing.EventSource>poskytuje základní třídu, ze které chcete vytvořit vlastního zprostředkovatele událostí. Obecně můžete vytvořit podtřídu <xref:System.Diagnostics.Tracing.EventSource> a `Write*` zabalit metody s vlastní metody událostí. Singleton vzor se obecně <xref:System.Diagnostics.Tracing.EventSource>používá pro každý .  
  
 Například třídu v následujícím příkladu lze použít k měření dvou charakteristik výkonu:  
  
- Čas do `App` konstruktoru třídy byl volán.  
  
- Čas do `MainPage` konstruktoru byl volán.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Je tu pár věcí, které si můžete všimnout. Nejprve singleton je `AppEventSource.Log`vytvořen v . Tato instance bude použita pro všechny protokolování. Za druhé, každá <xref:System.Diagnostics.Tracing.EventAttribute>metoda události má . To pomáhá nástrojové nástroje <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> přidružit index metody `AppEventSource`s metodou, která byla volána .  
  
 Všimněte si, že tyto události jsou čistě ilustrativní. Většina kódu aplikace se spustí po těchto událostech. Měli byste pochopit, které události v kódu odpovídají interakcím uživatelů, měřit je a vylepšovat tyto referenční hodnoty. Také samotné události protokolují pouze jednu instanci v čase. Často je užitečné mít spárované události spuštění a zastavení pro každou operaci. Při zkoumání spuštění aplikace start událost je obecně "Proces/Start" událost, která vydává operační systém.  
  
 Předpokládejme například, že vytváříte čtečku RSS. Několik zajímavých míst k přihlášení události jsou:  
  
- Při prvním vykreslení hlavní stránky.  
  
- Když jsou staré scénáře RSS dekonstruovány z místního úložiště.  
  
- Když vaše aplikace začne synchronizovat nové příběhy.  
  
- Až vaše aplikace dokončí synchronizaci nových příběhů.  
  
 Instrumentace aplikace je jednoduché: Stačí zavolat příslušnou metodu na odvozené třídy. Pomocí `AppEventSource` z předchozího příkladu můžete instrumentovat aplikaci takto:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Když je aplikace instrumentovaná, jste připraveni shromažďovat události.  
  
## <a name="gathering-events-with-perfview"></a>Shromažďování událostí pomocí perfview  
 PerfView používá Události ETW, které vám pomohou provést všechny druhy vyšetřování výkonu ve vaší aplikaci. Obsahuje také konfigurační grafické uživatelské rozhraní, které umožňuje zapnout nebo vypnout protokolování pro různé typy událostí. PerfView je bezplatný nástroj a lze jej stáhnout ze [služby Stažení softwaru](https://www.microsoft.com/download/details.aspx?id=28567). Další informace naleznete v [výukových videích PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
> PerfView nelze použít ke shromažďování událostí v systémech ARM. Chcete-li shromažďovat události v systémech ARM, použijte záznam výkonu systému Windows (WPR). Další informace naleznete [v příspěvku na blogu Vance Morrisona](https://docs.microsoft.com/archive/blogs/vancem/collecting-etwperfview-data-on-an-windows-rt-winrt-arm-surface-device).  
  
 Můžete také vyvolat PerfView z příkazového řádku. Chcete-li protokolovat pouze události od poskytovatele, otevřete okno příkazového řádku a zadejte příkaz:  
  
```console
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile
```  
  
 kde:  
  
 `-KernelEvents:Process`  
 Označuje, že chcete vědět, kdy proces spustí a zastaví. Pro aplikaci potřebujete událost Proces/Zahájení, aby ji bylo možné odečíst od jiných časů událostí.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Vypne ostatní zprostředkovatele, které PerfView ve výchozím nastavení zapne, a zapne zprostředkovatele MyCompany-MyApp.  (Hvězdička označuje, že se <xref:System.Diagnostics.Tracing.EventSource>jedná o .)  
  
 `collect outputFile`  
 Označuje, že chcete spustit sběr a uložit data do outputFile.etl.zip.  
  
 Spusťte aplikaci po spuštění PerfView. Při spouštění aplikace je třeba pamatovat na několik věcí:  
  
- Použijte sestavení verze, nikoli sestavení ladění. Sestavení ladění často obsahují další kontrolu chyb a kód zpracování chyb, který může způsobit, že vaše aplikace bude spuštěna pomaleji, než bylo očekáváno.  
  
- Spuštění aplikace s připojeným ladicím programem ovlivňuje výkon aplikace.  
  
- Systém Windows používá několik strategií ukládání do mezipaměti, aby urychlil časy spuštění aplikace. Pokud je vaše aplikace aktuálně uložena v mezipaměti a nemusí být načtena z disku, spustí se rychleji. Chcete-li zajistit konzistenci, spusťte a zavřete aplikaci několikrát před měřením.  
  
 Když spustíte aplikaci tak, aby PerfView můžete shromažďovat vyzařované události, zvolte tlačítko **Zastavit kolekci.** Obecně byste měli zastavit shromažďování před zavřením aplikace, takže nezískáte cizí události. Pokud však měříte výkon vypnutí nebo odpružení, budete chtít pokračovat ve sběru.  
  
## <a name="displaying-the-events"></a>Zobrazení událostí  
 Chcete-li zobrazit události, které již byly shromážděny, otevřete pomocí perfview soubor .etl nebo .etl.zip, který jste vytvořili, a zvolte **Události**. ETW bude shromažďovat informace o velkém počtu událostí, včetně událostí z jiných procesů. Chcete-li zaměřit šetření, vyplňte v zobrazení událostí následující textová pole:  
  
- Do pole **Filtr procesu** zadejte název aplikace (bez možnosti ".exe").  
  
- V poli **Filtr typů** `Process/Start | MyCompany-MyApp`událostí zadejte . Tím nastavíte filtr pro události z MyCompany-MyApp a události Jádro Windows/Proces/Start.  
  
 Vyberte všechny události uvedené v levém podokně (Ctrl-A) a zvolte klávesu **Enter.** Nyní byste měli být schopni vidět časová razítka z každé události. Tato časová razítka jsou relativní vzhledem k začátku trasování, takže je třeba odečíst čas každé události od počátečního času procesu k identifikaci uplynulého času od spuštění. Pokud pomocí kombinace kláves Ctrl+Click vyberete dvě časová razítka, zobrazí se rozdíl mezi nimi zobrazený na stavovém řádku v dolní části stránky. Díky tomu je snadné zobrazit uplynulý čas mezi dvěma událostmi na displeji (včetně spuštění procesu). Můžete otevřít místní nabídku pro zobrazení a vybrat z řady užitečných možností, jako je export do souborů CSV nebo otevření aplikace Microsoft Excel pro uložení nebo zpracování dat.  
  
 Opakováním postupu pro původní aplikaci i verzi, kterou jste vytvořili pomocí řetězce nástrojů .NET Native, můžete porovnat rozdíl ve výkonu.   Nativní aplikace .NET se obvykle spouštějí rychleji než non-.NET nativní aplikace. Pokud máte zájem o kopání hlouběji, PerfView můžete také identifikovat části kódu, které berou nejvíce času. Pro více informací se podívejte na [kurzy PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) nebo si přečtěte [položku blogu Vance Morrisona](https://docs.microsoft.com/archive/blogs/vancem/publication-of-the-perfview-performance-analysis-tool).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Tracing.EventSource>
