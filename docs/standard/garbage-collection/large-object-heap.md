---
title: Haldy velkých objektů v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dfe3fdbf71918a7ed2b6dccca24f58688bc14f2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617751"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Haldy velkých objektů v systémech Windows

.NET systému uvolňování paměti (GC) vyfiltruje objekty do malé a velké objekty. Je-li objekt velké, některé z jeho atributy výrazný nárůst více než pokud objekt je malý. Kompresi –, který se kopírování v paměti jinde v haldě – například může být nákladné. Z tohoto důvodu systému uvolňování paměti .NET umístí velkých objektů haldy pro velké objekty (loh modulem GC). V tomto tématu se podíváme na velkých objektových haldách do hloubky. Probereme, co splňuje podmínky objektu jako velkého objektu, jak se shromažďují tyto velké objekty a jaký druh důsledky velké objekty výkonu uložit.

> [!IMPORTANT]
> Toto téma popisuje haldy velkých objektů v rozhraní .NET Framework a .NET Core využívající pouze systémy Windows. Nezahrnuje LOH systémem implementace .NET na jiných platformách.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak objekt končí na velkých objektových haldách a jak je popisovačů GC

Pokud objekt je větší než nebo rovna hodnotě o velikosti 85 000 bajtů, se považuje za velké objekty. Toto číslo bylo určeno optimalizace výkonu. Požadavek na přidělení objektu je o velikosti 85 000 nebo více bajtů, modul runtime se přiděluje na velkých objektových haldách.

Vysvětlení, co to znamená, je užitečné si prohlédnout některé základní informace o uvolňování paměti .NET.

Uvolňování paměti .NET je generační kolekcí. Má tři generace: 0. generace 1. generace a 2. generace. Důvodem pro 3 generací je, že v dobře vyladit aplikaci, většina kostka objekty v gen0. V serveru aplikaci, byste například přidělení související s každou žádostí kostka, po dokončení požadavku. Žádosti o přidělení vydávaných za pochodu vytvořit do gen1 a kostka existuje. V podstatě gen1 funguje jako vyrovnávací paměť mezi mladé objekt oblasti a oblasti s dlouhým poločasem rozpadu objektu.

Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životního cyklu, může být povýšen na 1. generace nebo generation2. Velké objekty jsou vždy přiděleny v 2. generace.

Velké objekty patří do 2. generace, protože jsou shromažďovány pouze během shromažďování generace 2. Pokud generace jsou shromažďovány, shromažďují se také všech mladších generation(s). Například při uvolnění GC 1. generace dojde, se shromažďují i generace 1 a 0. A při uvolnění GC 2. generace dojde, celý haldy jsou shromažďovány. Z tohoto důvodu se také nazývá uvolnění GC 2. generace *úplné uvolňování paměti*. Tento článek odkazuje na 2. generace uvolňování paměti namísto úplný úklid GC, ale podmínky jsou zaměnitelné.

Generace poskytují logické zobrazení haldy uvolňování paměti. Fyzicky živé objekty ve spravované haldě segmenty. A *spravované haldě segmentu* se považuje blok paměti, která rezervuje GC z operačního systému pomocí volání [VirtualAlloc funkce](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jménem spravovaného kódu. Při načtení modulu CLR uvolňování paměti přiděluje dva segmenty počáteční haldy: jeden pro malé objekty (haldy malých objektů, nebo SOH) a jeden pro velké objekty (haldy pro velké objekty).

Přidělení požadavky splněny pak vložením spravované objekty v těchto segmentech spravované haldě. Pokud je objekt menší než o velikosti 85 000 bajtů, přejde na segment pro SOH; v opačném případě přejde LOH segmentu. Segmenty usilujeme o to (do menších bloků) jako další a další objekty přidělovány na ně.
Pro prohlášení o stavu objekty, které byly zachovány při uvolnění GC jsou povýšeny do příští generace. Objekty, které byly zachovány při shromažďování generace 0 jsou nyní považovány za objekty generace 1 a tak dále. Ale objekty, které byly zachovány při generování nejstarší jsou stále považovány za nejstarší generování. Jinými slovy jsou zachované objekty z 2. generace 2. generace objekty; a jsou zachované objekty z LOH LOH objekty, (které jsou shromážděné pomocí gen2).

Uživatelský kód můžete pouze přidělit v generaci 0 (malých objektů) nebo LOH (velkých objektů). Pouze pro uvolňování paměti může "přidělení paměti pro" objekty v 1. generace (podporou zachované objekty z 0. generace) a 2. generace (podporou zachované objekty z generací 1 a 2).

Při uvolňování paměti se aktivuje, GC trasování prostřednictvím živé objekty a komprimuje je. Ale protože je nákladná záležitost komprimace GC *přesune* LOH; usnadňuje volný seznam mimo neživými objekty, které lze znovu použít později ke splnění požadavků na přidělení velkého objektu. Sousední neživými objekty jsou provedeny do jednoho objektu zdarma.

.NET core a .NET Framework (od verze rozhraní .NET Framework 4.5.1) patří <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> vlastnost, která umožňuje uživatelům určit, že LOH má probíhat během další úplné blokující uvolňování paměti. A v budoucnu se mohou rozhodnout automaticky komprimovat LOH .NET. To znamená, že pokud přidělení paměti pro velké objekty a ujistěte se, že nelze přesunout, by měl stále připnete je.

Obrázek 1 ukazuje scénář, kde tvoří GC 1. generace za GC 0. generace první kde `Obj1` a `Obj3` generace 2 po první 1. generace uvolňování paměti forms jsou neaktivní a kde `Obj2` a `Obj5` jsou neaktivní. Všimněte si, že to a na následujících obrázcích jsou jen jako ukázka; obsahují velmi málo objekty kterého pochopíte, co se stane, že na haldě. Ve skutečnosti jsou celou řadu dalších objektů obvykle součástí serverem globálního katalogu.

![Obrázek 1: Uvolňování paměti generace 0 a 1. generace GC](media/loh/loh-figure-1.jpg)  
Obrázek 1: Generace 0 a 1. generace GC.

Obrázek 2 ukazuje, že po 2. generace GC které si všimli, že `Obj1` a `Obj2` jsou neaktivní, GC forms souvislých volného místa, nedostatek paměti, která používá pravděpodobně obsazena `Obj1` a `Obj2`, která byla použita k vyřízení požadavku na přidělení pro `Obj4`. Mezera za poslední objekt `Obj3`na konci segmentu slouží také ke splnění požadavků na přidělení.

![Obrázek 2: po uvolňování paměti generace 2](media/loh/loh-figure-2.jpg)  
Obrázek 2: po uvolnění GC 2. generace

Pokud není k dispozici dostatek volného místa pro plnění požadavků na přidělení velké objekty, uvolňování paměti se nejprve pokusí získat další segmenty z operačního systému. Pokud selže, spustí 2. generace uvolňování paměti v naději, uvolněte nějaké místo.

Během 1. generace nebo 2. generace uvolňování paměti, uvolňování paměti uvolní segmenty, které mají na ně žádné živé objekty zpět do operačního systému pomocí volání [funkce VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx). Mezera za poslední živé objekt na konec segmentu je zrušeny (s výjimkou na dočasný segment, ve kterém gen0/gen1 za provozu, ve kterém systému uvolňování paměti zachovat některé potvrzené, protože se být přidělování vaší aplikace v něm hned). A bezplatný prostory stále potvrdit, když dojde k jejich vynulování, což znamená, že není nutné zapisovat data v nich zpět na disk operačního systému.

Vzhledem k tomu, LOH se shromažďují, pouze během GC 2. generace, můžete segmentu LOH uvolněna pouze během těchto uvolňování paměti. Obrázek 3 ukazuje scénář, ve kterém systému uvolňování paměti uvolní jeden segment (segment 2) zpět do operačního systému a rozváže více místa na zbývající segmenty. Pokud je třeba použít zrušeny místa na konci segmentu pro splnění požadavků na přidělení velkého objektu, potvrzení paměti znovu. (Vysvětlení rozvázání/potvrzení, naleznete v dokumentaci k [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).

![Obrázek 3: LOH po uvolňování paměti generace 2](media/loh/loh-figure-3.jpg)  
Obrázek 3: LOH po 2. generace GC

## <a name="when-is-a-large-object-collected"></a>Když se shromažďují velké objekty

Obecně platí globální Katalog dojde, pokud jeden z následujících podmínek následující 3 se stane:

- Přidělování překračuje generace 0 nebo velkého objektu prahovou hodnotu.

  Prahová hodnota je vlastnost generace. Prahová hodnota pro generace je nastavena, když uvolňování paměti přiděluje objekty do něj. Pokud je překročena prahová hodnota, globální Katalog se aktivuje v této generací. Při přidělování malých nebo velkých objektů můžete využívat 0. generace a LOH prahové hodnoty, v uvedeném pořadí. Při uvolňování paměti přiděluje do generace 1 a 2, využívá jejich prahové hodnoty. Tyto prahové hodnoty je dynamicky vyladěná po spuštění programu.

  To je obvyklý případ; Většina GC dojít kvůli přidělení na spravované haldě.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána.

  Pokud konstruktor bez parametrů <xref:System.GC.Collect?displayProperty=nameWithType> metoda je volána nebo jiné přetížení se předá <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, jsou shromažďovány LOH spolu se zbývajícími spravované haldě.

- Systém je v případě nedostatku paměti.

  K tomu dojde, když systému uvolňování paměti obdrží oznámení vysoký poměr paměti z operačního systému. Pokud uvolňování domnívá, že to 2. generace GC bude produktivní, spustí jednu.

## <a name="loh-performance-implications"></a>Rozbor LOH výkonu

Přidělení na haldu velkých objektů dopad na výkon následujícími způsoby.

- Přidělování nákladů.

  Modul CLR provede záruku, že se vymaže paměti pro každý nový objekt, že poskytuje navýšení kapacity. To znamená, že přidělování nákladů ve velkém objektu je zcela léta dominovaly paměti vymazání (Pokud aktivuje GC). Pokud trvá 2 cykly zrušte jeden bajt, trvá 170,000 cykly zrušte nejmenší velkého objektu. Paměť objektu 16MB na počítači s 2GHz vymazáním trvá přibližně 16ms. To je docela rozsáhlá náklady.

- Kolekce nákladů.

  Protože LOH a 2. generace jsou shromažďovány společně, pokud je překročena mezní hodnota buď jeden z kolekce generace 2 se aktivuje. Pokud generace, které se z důvodu LOH aktivuje 2 kolekce, 2. generace nebudou nutně mnohem menší po uvolňování paměti. Pokud v 2. generace není množství dat, to má minimální dopad. Ale pokud generace 2 je velká, může to způsobit problémy s výkonem Pokud mnoho GC 2. generace se aktivuje. Mnoho velkých objektů jsou přiděleny velmi dočasný a máte velký SOH, může spotřebovat příliš mnoho času provádění GC. Kromě toho přidělování nákladů můžete ve skutečnosti přidání registrace Pokud uchováváte přidělování a volnost velmi velkých objektů.

- Prvky pole s typy odkazů.

  Pole (velmi zřídka dochází k instanci objekt, který je ve skutečnosti velký) jsou obvykle velmi velké objekty na LOH. Pokud jsou prvky pole bohatého na odkaz, budou vám účtovány náklady, které není k dispozici, pokud nejsou prvky bohatého na odkaz. Pokud element neobsahuje žádné odkazy, systému uvolňování paměti nemusí vůbec projít pole. Například pokud použijete pole k uložení uzly v binární strom, jeden ze způsobů implementace je k odkazování na uzlu vpravo a vlevo uzel skutečné uzly:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Pokud `num_nodes` je velké systému uvolňování paměti musí projít aspoň dva odkazy na jeden element. Alternativním přístupem je index pravém a levém uzlů úložiště:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Namísto odkazování data vlevo uzel jako `left.d`, můžete si ji jako `binary_tr[left_index].d`. A systému uvolňování paměti nemusí podívat se na všechny odkazy pro uzel doleva a doprava.

Mimo tři faktory jsou obvykle mnohem závažnější než třetí první dva. Z tohoto důvodu doporučujeme vám, že přidělíte fond velkých objektů, které můžete použít namísto přidělení dočasné ty.

## <a name="collecting-performance-data-for-the-loh"></a>Shromažďování dat výkonu pro LOH

Předtím, než můžete shromáždit údaje o výkonu pro konkrétní oblasti, můžete byste už mít provedli následující:

1. Najít důkaz, že by měl být díváte v této oblasti.

2. Vyčerpání další oblasti, které znáte nástroje, aniž byste hledání nic, které může vysvětlovat problému s výkonem, které jste viděli.

Najdete v blogovém [porozumět danému problému, než se pokusíte na vyhledání řešení](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) Další informace o základní informace o paměti a procesoru.

Můžete použít následující nástroje ke shromažďování dat o výkonu LOH:

- [Čítače výkonu paměti .NET CLR](#net-clr-memory-performance-counters)

- [Události trasování událostí pro Windows](#etw-events)

- [Ladicí program](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Čítače výkonu paměti .NET CLR

Tyto čítače výkonu jsou obvykle dobrý první krok při zkoumání problémů s výkonem (i když vám doporučujeme použít [události trasování událostí pro Windows](#etw)). Konfigurace sledování výkonu tak, že přidáte čítače, které potřebujete, jak je vidět na obrázku 4. Ty, které jsou relevantní pro LOH jsou:

- **Úklidy 2.**

   Zobrazí počet, kolikrát od spuštění procesu došlo k 2. generace GC. Hodnota čítače je zvýšena na konci kolekce generace 2 (také nazývané úplného uvolňování paměti kolekce). Tento čítač zobrazí naposledy zjištěnou hodnotu.

- **Velikost velkých objektových haldách**

   Zobrazí aktuální velikost v bajtech, včetně volné místo LOH. Tento čítač je aktualizován na konci uvolnění, ne při každém přidělení.

Běžný způsob, jak zobrazit čítače výkonu je pomocí sledování výkonu (perfmon.exe). Pomocí "Přidat čítače" přidat čítač zajímavé pro procesy, které vás zajímají. Data čítačů výkonu můžete uložit do souboru protokolu, jak je vidět na obrázku 4.

![Obrázek 4: Přidání čítačů výkonu.](media/loh/perfcounter.png)  
Obrázek 4: LOH po 2. generace GC

Čítače výkonu může být dotazována také prostřednictvím kódu programu. Řada lidí je shromažďovat tímto způsobem jako součást svých rutinní proces testování. Při jejich zjištění čítače nahraďte hodnotami, které jsou neobvyklého, používají jiným způsobem získat podrobnější údaje, které pomáhají při šetření.

> [!NOTE]
> Doporučujeme, abyste místo výkonu použít trasování událostí pro Windows čítače, protože trasování událostí pro Windows poskytuje mnohem bohatší informace.

### <a name="etw"></a>Trasování událostí pro Windows

Poskytuje širokou škálu události trasování událostí, které vám pomohou pochopit, co dělá haldy systému uvolňování paměti a proč. V následujících příspěvcích na blogu ukazují, jak shromažďovat a pochopit uvolňování paměti události trasování událostí pro Windows:

- [Události trasování událostí pro Windows uvolňování paměti – 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)

- [Události trasování událostí pro Windows uvolňování paměti – 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)

- [Události trasování událostí pro Windows uvolňování paměti – 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)

- [Události trasování událostí pro Windows uvolňování paměti – 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)

K identifikaci nadměrné generace GC 2 způsobena dočasné LOH přidělení, podívejte se na sloupce důvod aktivace pro GC. Pro jednoduchý test, který přiděluje jenom dočasné velké objekty, lze shromažďovat informace o události trasování událostí pro Windows s tímto [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) příkazového řádku:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Výsledkem je přibližně takto:

![Obrázek 5: Zkoumání událostí ETW pomocí nástroje PerfView](media/loh/perfview.png)  
Obrázek 5: Události trasování událostí pro Windows zobrazí, pomocí nástroje PerfView

Jak vidíte, jsou všechny GC 2. generace GC a všechny jsou aktivované pomocí AllocLarge, což znamená, že přidělování ve velkém objektu aktivuje toto uvolňování paměti. Víme, že jsou tyto přidělení dočasné vzhledem k tomu, **míra přežití LOH %** říká sloupce 1 %.

Můžete shromažďovat další události trasování událostí pro Windows, které informují vás, kteří přidělené tyto velké objekty. Na příkazovém řádku následující:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

shromažďuje události AllocationTick, která se aktivuje přibližně každých 100 kB za přidělení. Jinými slovy událost se aktivuje pokaždé, když je přiděleno ve velkém objektu. Pak můžete se podívat na jedno zobrazení alokační haldy uvolňování paměti, které zobrazují zásobníky volání, která přidělena velké objekty:

![Obrázek 6: Alokační haldy uvolňování paměti zobrazení](media/loh/perfview2.png)  
Obrázek 6: Alokační haldy uvolňování paměti zobrazení

Jak je vidět, to je velmi jednoduchý test, který právě přiděluje rozsáhlé objekty z jeho `Main` metoda.

### <a name="a-debugger"></a>Ladicí program

Pokud vše, co musíte je výpis paměti a je třeba podívat, jaké objekty jsou skutečně na LOH, můžete použít [rozšíření ladění SoS](http://msdn2.microsoft.com/ms404370.aspx) poskytované rozhraní .NET.

> [!NOTE]
> Příkazy ladění, které jsou uvedené v této části se vztahují na [ladicích programů Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Následuje ukázkový výstup z analýzy LOH:

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů. Mezi 023e1000 adresy a 033db630 8,008,736 bajtů obsazena pole <xref:System.Object?displayProperty=nameWithType> objekty, budou obsazeny 6,663,696 bajtů podle pole <xref:System.Byte?displayProperty=nameWithType> objekty a 2,081,792 bajtů obsazena volného místa.

V některých případech ladicí program ukazuje, že celková velikost LOH menší než o velikosti 85 000 bajtů. K tomu dochází, protože samotný modul runtime používá LOH přidělit některé objekty, které jsou menší než ve velkém objektu.

Vzhledem k tomu, že není setřepána LOH, někdy LOH je thoought zdroj fragmentace. Fragmentace znamená, že:

- Fragmentace spravované haldě, které jsou označeny množství volného místa mezi spravované objekty. V prodejní objednávky `!dumpheap –type Free` příkaz zobrazí množství volného místa mezi spravované objekty.

- Fragmentace adresního prostoru virtuální paměti (VM), což je paměť, označen jako `MEM_FREE`. Můžete ho získat s použitím různých příkazů ladicího programu v rámci windbg.

   Následující příklad ukazuje fragmentaci v prostoru virtuálních počítačů:

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

Je běžné zobrazíte fragmentace virtuálního počítače, způsobené dočasné velké objekty, které vyžadují systému uvolňování paměti se často získat nové spravované haldy segmenty z operačního systému a verze prázdných zpět do operačního systému.

Pokud chcete ověřit, zda LOH způsobuje fragmentaci na virtuální počítač, můžete nastavit zarážku na [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) a [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) zobrazíte jejich volání. Například pokud chcete zjistit, kdo se pokusil přidělení virtuální paměti bloky dat větší než 8MBB z operačního systému, můžete nastavit zarážku takto:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Tento příkaz do ladicího programu a zásobník volání pouze tehdy, pokud se zobrazí [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) se nazývá velikost alokační větší než 8 MB (0x800000).

Funkci přidali CLR 2.0 *VM Hoarding* , může být užitečné pro scenarious kde segmenty (včetně velkých i malých objektů haldy) jsou často získaných a vydání. K určení Hoarding virtuálního počítače, zadejte po spuštění příznak, který volá `STARTUP_HOARD_GC_VM` prostřednictvím hostujícího rozhraní API. Místo vydání prázdné segmenty zpět do operačního systému, CLR rozváže paměti v těchto segmentech a umístí na seznam pohotovostním režimu. (Všimněte si, že modul CLR nebude provést pro segmenty, které jsou moc velká.) Modul CLR později použije tyto segmenty splňovat nové požadavky segmentu. Příště, že vaše aplikace potřebuje nový segment CLR používá jednu z tohoto seznamu pohotovostní Pokud nemůže najít takový, který je dostatečně velký.

Hoarding virtuálního počítače je také užitečné pro aplikace, které chcete opřete se o segmenty, které už získali, jako je například některé serverové aplikace, které jsou dominantní aplikace běžící na systému, aby se zabránilo nedostatek paměti výjimky.

Důrazně doporučujeme při použití této funkce zajistit, že vaše aplikace má využití poměrně stálé paměti pečlivě otestovat aplikaci.
