---
title: Měření zlepšení spuštění pomocí .NET Native
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9546ddd12decb7457f4ff890658e2725a8b9dabe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941741"
---
# <a name="measuring-startup-improvement-with-net-native"></a>Měření zlepšení spuštění pomocí .NET Native
.NET Native významně vylepšuje dobu spouštění aplikací. Toto vylepšení je zvláště patrné na přenosném zařízení s nízkou spotřebou a složitých aplikacích. Toto téma vám pomůže začít se základní instrumentací potřebnou k měření tohoto vylepšení při spouštění.  
  
 Aby se usnadnilo zkoumání výkonu, .NET Framework a Windows používají architekturu událostí nazvanou trasování událostí pro Windows (ETW), která umožňuje vaší aplikaci upozorňovat nástroje, když dojde k událostem. Pak můžete pomocí nástroje s názvem PerfView snadno zobrazit a analyzovat události ETW. V tomto tématu se dozvíte, jak:  
  
- <xref:System.Diagnostics.Tracing.EventSource> Použijte třídu k vygenerování událostí.  
  
- Pomocí PerfView shromážděte tyto události.  
  
- Tyto události můžete zobrazit pomocí PerfView.  
  
## <a name="using-eventsource-to-emit-events"></a>Použití EventSource k vygenerování událostí  
 <xref:System.Diagnostics.Tracing.EventSource>poskytuje základní třídu, ze které se má vytvořit vlastní zprostředkovatel událostí. Obecně vytvoříte podtřídu <xref:System.Diagnostics.Tracing.EventSource> a `Write*` zabalíte metody s vlastními metodami událostí. Vzor typu Singleton se obecně používá pro každý <xref:System.Diagnostics.Tracing.EventSource>z nich.  
  
 Například třída v následujícím příkladu může být použita k měření dvou charakteristik výkonu:  
  
- Čas volání konstruktoru `App` třídy.  
  
- Čas, kdy byl `MainPage` konstruktor volán.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Tady si můžete všimnout několika věcí. Nejprve je vytvořen typ singleton v `AppEventSource.Log`. Tato instance se použije pro všechna protokolování. Druhý, každá metoda události má <xref:System.Diagnostics.Tracing.EventAttribute>. To pomáhá nástrojům přidružit index <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> metody k metodě, která byla `AppEventSource`volána.  
  
 Všimněte si, že tyto události jsou čistě ilustrativní. Po těchto událostech se spustí většina kódu aplikace. Měli byste pochopit, které události v kódu odpovídají interakcím uživatelů, měřit je a zlepšovat tyto srovnávací testy. Události samy protokolují také jedinou instanci v čase. Pro každou operaci je často vhodné párovat události spuštění a zastavení. Při kontrole spuštění aplikace je počáteční událost obecně událost "proces/spuštění", kterou operační systém generuje.  
  
 Předpokládejme například, že vytváříte čtečku RSS. Několik zajímavých míst pro protokolování události:  
  
- Při prvním vykreslení hlavní stránky.  
  
- Při deserializaci starých scénářů RSS z místního úložiště.  
  
- Když vaše aplikace začne synchronizovat nové příběhy.  
  
- Až aplikace dokončí synchronizaci nových scénářů.  
  
 Instrumentace aplikace je jednoduchá: Stačí volat odpovídající metodu pro odvozenou třídu. Pomocí `AppEventSource` předchozího příkladu můžete instrumentovat aplikaci následujícím způsobem:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Když je aplikace instrumentovaná, jste připraveni shromáždit události.  
  
## <a name="gathering-events-with-perfview"></a>Shromažďování událostí pomocí PerfView  
 PerfView využívá události trasování událostí pro Windows, které vám pomůžou dělat nejrůznější zkoumání výkonu v aplikaci. Obsahuje taky konfiguraci grafického uživatelského rozhraní, která umožňuje zapnout nebo vypnout protokolování pro různé typy událostí. PerfView je bezplatný nástroj, který je možné stáhnout z webu [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567). Další informace najdete v výukových [videech k PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
> PerfView se nedá použít ke shromažďování událostí v systémech ARM. K shromažďování událostí na systémy ARM použijte Windows Performance Record (WPR). Další informace najdete v [příspěvku na blogu Vance Morrison](https://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Můžete také vyvolat PerfView z příkazového řádku. Pokud chcete protokolovat pouze události od poskytovatele, otevřete okno příkazového řádku a zadejte příkaz:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 kde:  
  
 `-KernelEvents:Process`  
 Označuje, že chcete zjistit, kdy se proces spouští a zastavuje. Pro vaši aplikaci budete potřebovat událost proces/spuštění, aby bylo možné je odečíst od jiných časů události.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 Vypne ostatní poskytovatele, které PerfView ve výchozím nastavení zapne, a zapne poskytovatele spolecnosti-MyApp.  (Hvězdička indikuje, že se jedná <xref:System.Diagnostics.Tracing.EventSource>o.)  
  
 `collect outputFile`  
 Označuje, že chcete spustit shromažďování dat a uložit data do souboru Výstupní_soubor. ETL. zip.  
  
 Po spuštění PerfView spusťte svoji aplikaci. Při spouštění aplikace si pamatujte na pár věcí:  
  
- Použijte sestavení pro vydání, nikoli ladicí sestavení. Sestavení ladění často obsahují speciální kontrolu chyb a kód pro zpracování chyb, které můžou způsobit, že vaše aplikace bude běžet pomaleji, než se očekávalo.  
  
- Spuštění aplikace s připojeným ladicím programem má vliv na výkon aplikace.  
  
- Systém Windows používá k urychlení časů spouštění aplikací více strategií ukládání do mezipaměti. Pokud je vaše aplikace aktuálně uložená v mezipaměti a není nutné ji načítat z disku, spustí se rychleji. Abyste zajistili konzistenci, spusťte a zavřete aplikaci několikrát ještě předtím, než ji budete měřit.  
  
 Po spuštění aplikace tak, aby PerfView mohl shromažďovat vypouštěné události, klikněte na tlačítko **Zastavit shromažďování** . Obecně platí, že před zavřením aplikace byste měli zastavit shromažďování, abyste nedostali nadbytečné události. Pokud ale měříte výkon při vypnutí nebo pozastavení, budete chtít pokračovat v shromažďování.  
  
## <a name="displaying-the-events"></a>Zobrazení událostí  
 Chcete-li zobrazit události, které již byly shromážděny, pomocí PerfView otevřete soubor ETL nebo ETL. zip, který jste vytvořili, a vyberte možnost **události**. ETW bude shromažďovat informace o velkém počtu událostí, včetně událostí z jiných procesů. Chcete-li se zaměřit na šetření, vyplňte v zobrazení události následující textová pole:  
  
- V poli **Filtr procesu** zadejte název aplikace (bez ". exe").  
  
- V poli **Filtr typů událostí** zadejte `Process/Start | MyCompany-MyApp`. Tím se nastaví filtr pro události ze společnosti-MyApp a z události jádro/proces nebo spuštění systému Windows.  
  
 Vyberte všechny události uvedené v levém podokně (CTRL-A) a stiskněte klávesu **ENTER** . Nyní byste měli být schopni zobrazit časová razítka z každé události. Tato časová razítka jsou relativní ke spuštění trasování, takže je nutné odečíst čas každé události od počátečního času procesu k identifikaci uplynulého času od spuštění. Použijete-li k výběru dvou časových razítek kombinaci kláves Ctrl + kliknutí, uvidíte rozdíl mezi nimi ve stavovém řádku v dolní části stránky. To usnadňuje zobrazení uplynulého času mezi všemi dvěma událostmi v zobrazení (včetně spuštění procesu). Můžete otevřít místní nabídku pro zobrazení a vybrat z řady užitečných možností, jako je například export do souborů CSV nebo otevření aplikace Microsoft Excel pro uložení nebo zpracování dat.  
  
 Zopakováním postupu jak pro původní aplikaci, tak pro verzi, kterou jste vytvořili pomocí řetězce nástroje .NET Native, můžete porovnat rozdíl ve výkonu.   Aplikace .NET Native obecně začíná rychleji než non-.NET nativní aplikace. Pokud vás zajímá prozkoumá hlouběji, PerfView může také identifikovat části vašeho kódu, které se přebírají nejvíce času. Další informace najdete v výukových [kurzech k PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) nebo v [záznamu blogu pro Vance Morrison](https://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Tracing.EventSource>
