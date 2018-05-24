---
title: Halda velkého objektu v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: abb1f72a10a4aff448dea22b5c9415111c25eaab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a>Halda velkého objektu v systémech Windows

Systém uvolňování paměti .NET (GC) vyfiltruje objekty do malých a velkých objektů. Po velký objekt některé jeho atributy závažnější než pokud je objekt malá. Kompresi ho – který se kopírování v paměti jinde v haldě – například může být náročné. Z toho důvodu Garbage Collector v rozhraní .NET umístí rozsáhlé objekty v haldě velkého objektu (LOH). V tomto tématu se podíváme velkého objektu haldy podrobněji. Probereme co vyfiltrování objekt jako velkého objektu, jak se shromažďují tyto rozsáhlé objekty a co druh důsledky velké objekty výkonu použít.

> [!IMPORTANT]
> Toto téma popisuje velkého objektu haldy v rozhraní .NET Framework a .NET Core spuštěna pouze pro systémy Windows. Nepokrývá LOH systémem implementace rozhraní .NET na jiných platformách.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak objekt skončilo v haldě velkého objektu a jak je GC zpracovává

Pokud objekt je větší než nebo rovna 85,000 bajtů, považuje za velkého objektu. Toto číslo bylo určeno optimalizace výkonu. Při požadavku na přidělení objekt je pro 85,000 nebo více bajtů, modul runtime jí v haldě velkého objektu.

Zjistit, co to znamená, je užitečné k prozkoumání některých základní informace o GC rozhraní .NET.

Uvolňování paměti rozhraní .NET je generační kolekce. Má tři generace: generování 0, 1. generace a 2. generace. Důvodem pro 3 generace předpokládají, že v dobře ujít aplikaci, většina die objekty v gen0. V aplikaci pomocí serveru, by například přidělení související s každou žádostí kostka, po dokončení požadavku. Požadavky během letu přidělení vytvořit do gen1 a kostka existuje. V podstatě gen1 funguje jako vyrovnávací paměť mezi malí objekt oblasti a oblasti dlohotrvající objektu.

Malé objekty jsou vždy přidělené v generace 0 a v závislosti na své životnosti, může být převeden na generace 1 nebo generation2. Rozsáhlé objekty jsou vždy přidělené v 2. generace.

Rozsáhlé objekty patří do generace 2, protože jsou shromážděná pouze během 2. generace kolekce. Když jsou shromažďována generace, jeho mladší generation(s) se také shromažďují. Například když se stane GC 1. generace, se shromažďují obě generace 1 a 0. A když se stane GC 2. generace, jsou shromažďovány celou halda. Z tohoto důvodu se také nazývá GC 2. generace *úplné GC*. Tento článek odkazuje na 2. generace GC místo úplný úklid GC, ale podmínky jsou uvedeny zaměnitelné.

Generace poskytují logické zobrazení haldě GC. Fyzicky objekty existují v spravovaná halda segmenty. A *spravovaná halda segment* se považuje blok, paměti, která globální Katalog rezerv z operačního systému při volání [VirtualAlloc funkce](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jménem spravovaného kódu. Při načítání modulu CLR, globální Katalog přiděluje dva segmenty počáteční haldy: jeden pro malé objekty (malé objektu haldy, nebo SOH) a jeden pro velké objekty (velkého objektu haldy).

Přidělení požadavky jsou pak splněny umístěním spravované objekty v těchto spravovaná halda segmenty. Pokud se objekt menší než 85,000 bajtů, jsou uváděny v segmentu pro SOH; jinak jsou uváděny v LOH segmentu. Segmenty jsou (v menší bloky dat) jako informace a další objekty, které jsou přiděleny do nich.
Pro prohlášení o stavu objekty, které zůstanou platné i po globální Katalog povýšené na nové generace. Objekty, které zůstanou platné i po 0. generace kolekce jsou nyní považovány za objekty 1. generace a tak dále. Ale objekty, které zůstanou platné i po nejstarší generace jsou stále považování za nejstarší generování. Jinými slovy přesun z 2. generace jsou objekty 2. generace; a přesun z LOH jsou objekty LOH, (které se vybírají pomocí gen2). 

Uživatelský kód můžete přidělit pouze při generování, 0 (malé objekty) nebo LOH (rozsáhlé objekty). Pouze globální Katalog "přidělit" objekty v 1. generace (podporou přesun z generace 0) a generace 2 (podporou přesun z generace 1 a 2).

Když se aktivuje uvolňování paměti, globální Katalog trasování prostřednictvím živé objekty a zkomprimuje je. Ale protože je náročné, komprimace globální Katalog *přesune* LOH; umožňuje volné seznamu mimo neaktivní objekty, které lze znovu použít později pro uspokojení požadavků na přidělení velkého objektu. Sousední neaktivní objekty jsou vytvářeny do volného jeden objekt.

.NET core a rozhraní .NET Framework (od verze rozhraní .NET Framework 4.5.1) obsahují <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> vlastnost, která umožňuje uživatelům určit, že LOH má probíhat během další úplné blokování GC. A v budoucnu, mohou rozhodnout .NET compact LOH automaticky. To znamená, že pokud přidělit rozsáhlé objekty a ujistěte se, že nelze přesunout, by měl stále připnete je.

Obrázek 1 ukazuje scénář, kde globální Katalog forms generace 1 po GC 0. generace první kde `Obj1` a `Obj3` jsou neaktivní a forms generace 2 po GC 1. generace první kde `Obj2` a `Obj5` jsou neaktivní. Upozorňujeme, že toto a následující údaje jsou pouze pro účely obrázku; obsahují velmi několik objektů na lépe zobrazit, co se stane, že v haldě. Ve skutečnosti se obvykle podílejí celou řadu dalších objektů v globálním Katalogem.

![Obrázek 1: 0. generace GC a GC 1. generace](media/loh/loh-figure-1.jpg)   
Obrázek 1: Generace 0 a 1. generace GC.

Obrázek 2 ukazuje, že po GC 2. generace, která viděli `Obj1` a `Obj2` jsou neaktivní, globální Katalog forms souvislého volného místa, nedostatek paměti, která používá na kterém je umístěna `Obj1` a `Obj2`, který pak byl použit pro uspokojení požadavku na přidělení pro `Obj4`. Prostor po poslední objekt, `Obj3`, na konec segmentu lze také pro uspokojení požadavků na přidělení.
 
![Obrázek 2: po GC 2. generace](media/loh/loh-figure-2.jpg)  
Obrázek 2: po GC 2. generace

Pokud není k dispozici dostatek volného místa pro uložení požadavků na přidělení velkého objektu, globální Katalog napřed pokusí získat další segmenty z operačního systému. Pokud to nepomůže, aktivuje GC 2. generace v naděje z uvolněte místo.

Během generace 1 nebo 2. generace GC, bude systém uvolňování uvolní segmentech, které mají žádné objekty v za provozu na nich zpět do operačního systému při volání [virtualfree – funkce](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx). Prostor po poslední za provozu objekt na konec segmentu je nepotvrzená (s výjimkou v dočasných segmentu, kde gen0/gen1 za provozu, kde bude systém uvolňování ponechat některé potvrzené, protože bude možné přidělování vaší aplikace v ní hned). A volné prostory zůstanou potvrdit, když dojde k jejich vynulování, což znamená, že nemusí zapisovat data v nich zpět na disk operačního systému.

Vzhledem k tomu, že LOH se shromažďují pouze během GC 2. generace, může být LOH segment uvolněno pouze během globální Katalog. Obrázek 3 ukazuje scénář, kde bude systém uvolňování uvolní jednoho segmentu (segment 2) zpět do operačního systému a decommits více místa na zbývající segmenty. Pokud je třeba použít Nepotvrzená místa na konci tohoto segmentu pro uspokojení požadavků na přidělení velkého objektu, potvrdí paměť znovu. (Další informace o potvrzení nebo zruší, naleznete v dokumentaci k [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).
 
![Obrázek 3: LOH po GC 2. generace](media/loh/loh-figure-3.jpg)  
Obrázek 3: LOH po GC 2. generace

## <a name="when-is-a-large-object-collected"></a>Když se shromažďují velkého objektu?

Obecně platí globální Katalog dojde, pokud jeden z následujících podmínek následující 3 se stane:

- Přidělení překračuje generace 0 nebo velkého objektu prahovou hodnotu.

   Prahová hodnota je vlastností generace. Prahová hodnota pro generace nastavena při uvolňování paměti přidělí objekty do ní. Pokud je překročena prahová hodnota, aktivuje se v této generaci serverem globálního katalogu. Při přidělování objektů malý nebo velký, můžete využívat generace 0 a prahové hodnoty LOH, v uvedeném pořadí. Při uvolňování paměti přidělí do generace 1 a 2, využívá příslušné prahové hodnoty. Tyto prahové hodnoty jsou dynamicky přizpůsobená po spuštění programu.

   Toto je obvyklý případ; Většina GC dojít z důvodu přidělování v haldě spravované.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána.

   Pokud bez parametrů <xref:System.GC.Collect?displayProperty=nameWithType> metoda je volána nebo jiné přetížení, je předaná <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, jsou shromažďovány LOH spolu s ostatními spravovaná halda.

- Systém je v případě nedostatku paměti.

   K tomu dochází, když má systém uvolňování obdrží oznámení velkého množství paměti z operačního systému. Pokud garbage collector v se domnívá, že to GC 2. generace bude produktivní, aktivuje jeden.

## <a name="loh-performance-implications"></a>Ovlivnit výkon LOH

Přidělování v haldě velkého objektu dopad na výkon následujícím způsobem.

- Přidělení náklady.

   Modul CLR Díky záruku, že není zaškrtnuto paměti pro všechny nové objekty, že nabízí. To znamená, že náklady na přidělení velkého objektu je zcela ovládnutí paměti vymazání (Pokud aktivuje globální Katalog). Pokud bude trvat 2 cykly zrušte jeden bajt, trvá 170,000 cykly zrušte nejmenší velký objekt. Vymazání memmory objektu 16MB na počítači, 2GHz trvá přibližně 16ms. To je místo velkých náklady.

- Kolekce náklady.

   Protože LOH a 2. generace jsou seskupeny, pokud je překročena mezní hodnota některé z nich je, aktivuje se 2. generace kolekce. Pokud generování, které se z důvodu LOH aktivuje 2 kolekce, 2. generace nebudou nutně mnohem menší po globální Katalog. Pokud na 2. generace není množství dat, to má minimální dopad. Ale pokud generace 2 je velká, může to způsobit problémy s výkonem Pokud aktivaci mnoho GC 2. generace. Mnoho velkých objektů jsou přiděleny velmi dočasné a máte velké prohlášení o stavu, může výdaje příliš mnoho času provádění GC. Kromě toho náklady na přidělení můžete skutečně dohromady Pokud necháte přidělování, když necháte přejděte skutečně velkých objektů.

- Elementy pole s odkazové typy.

   Velmi velkých objektů na LOH jsou obvykle pole (je velmi výjimečných tak, aby měl instance objektu, který skutečně velké). Pokud jsou elementy pole odkaz bohaté, způsobuje náklady, které není k dispozici, pokud nejsou elementy bohaté odkaz. Pokud element neobsahuje žádné odkazy, bude systém uvolňování nemusí vůbec projít pole. Například pokud použijete pole k uložení uzly v binárního stromu, jedním ze způsobů implementaci je k odkazování na uzlu vlevo a vpravo uzlu skutečné uzly:

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   Pokud `num_nodes` je velký, bude systém uvolňování musí projít, aspoň dva odkazy na jeden element. Alternativní způsob je index pravé a levé uzly úložiště:

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   Místo odkazující data levém uzlu jako `left.d`, můžete použít informace jako `binary_tr[left_index].d`. A uvolňování nemusí podívejte se na všechny odkazy pro levý a pravý uzel.

Mimo třech faktorech jsou obvykle větších než třetí první dvě. Z toho důvodu doporučujeme, že přidělíte fond rozsáhlé objekty, které znovu použít místo přidělování dočasné ty. 

## <a name="collecting-performance-data-for-the-loh"></a>Shromažďování dat výkonu pro LOH

Předtím, než můžete shromažďovat údaje o výkonu pro určitou oblast, musí již uděláte následující:

1. Najít důkaz, že jste měli vyhledávání v této oblasti.

1. Další oblasti, které znáte služby, aniž byste hledání nic může vysvětlující problému s výkonem, které jste viděli vyčerpá.

Naleznete v blogu [problém pochopit, teprve pak zkuste najít řešení](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) Další informace o základní informace o paměti a procesoru.

Tyto nástroje můžete použít ke shromažďování dat na výkon LOH:

- [Čítače výkonu paměti .NET CLR](#net-clr-memory-performance-counters)

- [Události trasování událostí pro Windows](#etw-events)

- [Ladicí program](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Čítače výkonu paměti .NET CLR

Tyto čítače výkonu jsou obvykle dobrou prvním krokem při zkoumání problémů s výkonem (i když vám doporučujeme používat [události trasování událostí](#etw)). Nakonfigurujete sledování výkonu přidáním čítačů, které potřebujete, jak ukazuje obrázek 4. Ty, které jsou relevantní pro LOH jsou:

- **\# 2. generace kolekce**

   Zobrazí počet opakovaných 2. generace GC došlo od spuštění procesu. Hodnota čítače je zvýšena na konec kolekce 2. generace (také nazývané úplný uvolňování). Čítač zobrazí naposledy zjištěnou hodnotu.

- **Velká velikost objektu haldy**

   Zobrazí aktuální velikost v bajtech, včetně volné místo LOH. Toto počítadlo je aktualizováno na konci uvolňování, ne v každém přidělení.

Podívejte se na čítače výkonu běžný způsob je pomocí sledování výkonu (perfmon.exe). Pomocí "Přidat čítače" přidat čítač zajímavé pro procesy, které kterých vám nejvíc záleží. Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4.

![Obrázek 4: Přidání čítačů výkonu.](media/loh/perfcounter.png)    
Obrázek 4: LOH po GC 2. generace

Čítače výkonu může být dotazována také prostřednictvím kódu programu. Spousta lidí shromažďovat, je tímto způsobem v rámci své běžné testování procesu. Při jejich přímé čítače s hodnotami, které jsou neobvyklého, používají jiným způsobem získat podrobnější data, které pomáhají při šetření.

> [!NOTE]
> Doporučujeme, aby vám umožní používat události trasování událostí místo výkonu čítače, protože trasování událostí pro Windows poskytuje mnohem širší informace.

### <a name="etw"></a>Trasování událostí pro Windows

Uvolňování paměti poskytuje bohatou sadu události trasování událostí, které vám pomohou pochopit, co je to halda a proč. V následujících příspěvcích na blogu ukazují, jak shromažďovat a pochopit uvolňování paměti události trasování událostí pro Windows:

- [Události trasování událostí pro Windows GC - 1 ](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [Události trasování událostí pro Windows GC - 2](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [Události trasování událostí pro Windows GC - 3](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [Události trasování událostí pro Windows GC - 4](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

K identifikaci nadměrné generace 2 GC způsobeno dočasnou LOH přidělení, podívejte se na sloupce důvod aktivační událost pro GC. Pro jednoduchý test, který pouze přiděluje dočasné objekty velké, může shromažďovat informace o události trasování událostí s následující [nástroje PerfView](https://www.microsoft.com/download/details.aspx?id=28567) příkazového řádku:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Výsledkem je přibližně takto:
 
![Obrázek 5: Prozkoumání události trasování událostí pro Windows pomocí nástroje PerfView](media/loh/perfview.png)  
Obrázek 5: Události trasování událostí pro Windows zobrazí pomocí nástroje PerfView

Jak vidíte, jsou všechny GC 2. generace GC a se všechny spouštějí AllocLarge, což znamená, že přidělování velkého objektu aktivaci tato globální Katalog. Víme, že jsou tyto přidělení dočasné protože **LOH základními míra %** sloupec uvádí 1 %.

Můžete shromažďovat další události trasování událostí pro Windows, které zjistíte, kdo přidělené tyto velké objekty. Následující příkaz:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

shromažďuje AllocationTick událost, která je aktivována, přibližně každých 100 kB vhodné přidělení. Jinými slovy vyvolání události pokaždé, když je přidělen velkého objektu. Pak můžete najít v některém z alokační haldě GC zobrazení, která ukazují callstacks, která přidělena rozsáhlé objekty:
 
![Obrázek 6: Alokační haldě GC zobrazení](media/loh/perfview2.png)  
Obrázek 6: Alokační haldě GC zobrazení
 
Jak vidíte, to je velmi jednoduchý test, který právě přiděluje rozsáhlé objekty z jeho `Main` metoda.

### <a name="a-debugger"></a>Ladicí program

Pokud máte je výpis stavu paměti a potřebujete podívat, jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladění SoS](http://msdn2.microsoft.com/ms404370.aspx) poskytované .NET. 

> [!NOTE]
> Ladění příkazy uvedené v této části se vztahují na [ladicí programy Windows](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Následuje příklad výstupu z analýza LOH:

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

Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů. Mezi 023e1000 adresy a 033db630 8,008,736 bajtů obsazena pole <xref:System.Object?displayProperty=fullName> objekty, 6,663,696 bajtů jsou obsazena pole <xref:System.Byte?displayProperty=nameWithType> objekty a 2,081,792 bajtů obsazena volného místa.

V některých případech ladicí program ukazuje, že je celková velikost LOH je menší než 85,000 bajtů. K tomu dochází, protože modul runtime, samotné používá LOH přidělit některé objekty, které jsou menší než velkého objektu.

Vzhledem k tomu LOH není komprimován, někdy LOH je thoought jako zdroj fragmentace. Fragmentace znamená:

- Fragmentace spravovaná halda, což je indikován množství volného místa mezi spravovaných objektů. V SoS `!dumpheap –type Free` příkaz zobrazí množství volného místa mezi spravovaných objektů.

- Fragmentace adresního prostoru virtuální paměti (VM), což je paměť označen jako `MEM_FREE`. Můžete ho získat pomocí různých příkazů ladicího programu v windbg.

   Následující příklad ukazuje fragmentace v prostoru virtuálních počítačů:

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

Je dnes běžné zobrazíte fragmentace virtuálního počítače, způsobené dočasné velkých objektů, které vyžadují uvolňování často získat nové spravovaná halda segmenty z operačního systému a verze prázdných zpět do operačního systému.

Pokud chcete ověřit, zda LOH způsobuje fragmentace virtuálních počítačů, můžete nastavit zarážky [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) a [virtualfree –](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) zobrazíte, který je volání. Například pokud chcete zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážky takto:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Tento příkaz do ladicího programu a zobrazuje jenom pokud zásobník volání [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) je volán s velikost alokační větší než 8 MB (0x800000).

Přidat funkci CLR 2.0 *Hoarding virtuálních počítačů* , může být užitečná pro scenarious kde segmentuje (včetně velkých a malých objektu haldách) jsou často získali a vydání. Pokud chcete zadat Hoarding virtuálního počítače, zadejte příznak spuštění `STARTUP_HOARD_GC_VM` prostřednictvím rozhraní API hostování. Místo vydání prázdný segmenty zpět do operačního systému, modul CLR decommits paměť na tyto segmenty a vloží je na seznamu pohotovostní. (Všimněte si, že modulu CLR není tomu segmentů, které jsou příliš velké.) Modul CLR později používá tyto segmenty vyhovět nové žádosti o segmentu. Další čas, které aplikace potřebuje nový segment, modul CLR používá jednu z tohoto seznamu pohotovostní Pokud nemůže najít ten, který je dost velký.

Virtuální počítač hoarding je také užitečné pro aplikace, které má být blokování do segmentů, které se již získal, zvolte například některé serveru aplikací, které jsou dominantní aplikace běžící v systému, aby se zabránilo nedostatek paměti výjimky.

Důrazně doporučujeme při použití této funkce zajistit, že aplikace má využití poměrně stálé paměti pečlivě otestovat aplikaci.
