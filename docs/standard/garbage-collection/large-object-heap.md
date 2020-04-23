---
title: Haldy velkých objektů (LOH) v systému Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102265"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Haldy velkých objektů v systémech Windows

Systém uvolňování paměti .NET (GC) rozděluje objekty na malé a velké objekty. Pokud je objekt velký, některé jeho atributy se stanou významnějšími než v případě, že je objekt malý. Například komprimace,&mdash;která je, kopírování v paměti&mdash;jinde na haldě může být nákladné. Z tohoto důvodu systém uvolňování umístí velké objekty na haldy velkých objektů (LOH). Tento článek popisuje, co kvalifikuje objekt jako velký objekt, jak velké objekty jsou shromažďovány a jaký druh výkonu důsledky velké objekty uložit.

> [!IMPORTANT]
> Tento článek popisuje haldu velkých objektů v rozhraní .NET Framework a .NET Core spuštěné pouze v systémech Windows. Nezahrnuje LOH spuštěné na implementacích .NET na jiných platformách.

## <a name="how-an-object-ends-up-on-the-loh"></a>Jak objekt skončí na LOH

Pokud je objekt větší nebo roven velikosti 85 000 bajtů, je považován za velký objekt. Toto číslo bylo určeno laděním výkonu. Pokud je požadavek na přidělení objektu pro 85 000 nebo více bajtů, přiděluje jej runtime na haldě velkého objektu.

Chcete-li pochopit, co to znamená, je užitečné prozkoumat některé základy o uvolňování paměti.

Systém uvolňování paměti je generační kolektor. Má tři generace: generace 0, generace 1 a generace 2. Důvodem pro mít 3 generace je, že v dobře vyladěné aplikaci, většina objektů zemře v gen0. Například v serverové aplikaci by přidělení přidružená ke každému požadavku měla po dokončení požadavku zemřít. In-letu přidělení žádosti bude dělat to do gen1 a zemřít tam. Gen1 v podstatě funguje jako nárazník mezi oblastmi mladých objektů a oblastmi objektů s dlouhou životností.

Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životnosti může být povýšen na generaci 1 nebo generace2. Velké objekty jsou vždy přiděleny v generaci 2.

Velké objekty patří do generace 2, protože jsou shromažďovány pouze během kolekce generace 2. Když generace jsou shromažďovány, všechny jeho mladší generace jsou také shromažďovány. Například když generace 1 GC se stane, jak generace 1 a 0 jsou shromažďovány. A když generace 2 GC se stane, celá halda je shromažďována. Z tohoto důvodu generace 2 GC se také nazývá *úplné GC*. Tento článek odkazuje na generace 2 GC namísto úplné GC, ale podmínky jsou zaměnitelné.

Generace poskytují logický pohled na haldu GC. Fyzicky objekty žijí ve spravovaných segmentech haldy. Segment *spravované haldy* je blok paměti, který gc rezervy z operačního systému voláním [VirtualAlloc funkce](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jménem spravovaného kódu. Při načtení CLR GC přiděluje dva počáteční haldy segmenty: jeden pro malé objekty (haldy malý objekt nebo SOH), a jeden pro velké objekty (velký objekt haldy).

Požadavky na přidělení jsou pak splněny umístěním spravované objekty na tyto segmenty spravované haldy. Pokud je objekt menší než 85 000 bajtů, je umístěn na segment pro SOH; v opačném případě je umístěn na segment LOH. Segmenty jsou potvrzeny (v menších blocích), protože na ně je přidělováno více a více objektů.
Pro SOH objekty, které přežijí GC jsou povýšeni na další generaci. Objekty, které přežijí kolekci generace 0, jsou nyní považovány za objekty generace 1 a tak dále. Objekty, které přežijí nejstarší generaci, jsou však stále považovány za nejstarší generace. Jinými slovy, přeživší z generace 2 jsou objekty generace 2; a přeživší z LOH jsou LOH objekty (které jsou shromažďovány s gen2).

Uživatelský kód lze přidělit pouze v generaci 0 (malé objekty) nebo LOH (velké objekty). Pouze GC může "přidělit" objekty v generaci 1 (podporou přeživších z generace 0) a generace 2 (podporou přeživších z generací 1 a 2).

Při uvolnění paměti je spuštěna, GC trasování prostřednictvím živých objektů a komprimuje je. Ale protože zhutnění je drahé, GC *zametá* LOH; vytvoří volný seznam z mrtvých objektů, které lze později znovu použít k uspokojení požadavků na přidělení velkých objektů. Přilehlé mrtvé objekty jsou rozděleny do jednoho volného objektu.

.NET Core a .NET Framework (počínaje rozhraním .NET <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> Framework 4.5.1) zahrnují vlastnost, která uživatelům umožňuje určit, že loh by měl být komprimován během dalšího úplného blokování GC. A v budoucnu .NET může rozhodnout o komprimovat LOH automaticky. To znamená, že pokud přidělujete velké objekty a chcete se ujistit, že se nepohybují, měli byste je stále připnout.

Obrázek 1 znázorňuje scénář, kde GC tvoří generace `Obj1` `Obj3` 1 po první generaci 0 GC kde a `Obj2` `Obj5` jsou mrtvé a tvoří generace 2 po první generaci 1 GC kde a jsou mrtvé. Všimněte si, že tyto a následující obrázky jsou pouze pro ilustrační účely; obsahují jen velmi málo objektů, aby lépe ukázat, co se děje na haldě. Ve skutečnosti mnoho dalších objektů jsou obvykle zapojeny do GC.

![Obrázek 1: A gen 0 GC a gen 1 GC](media/loh/loh-figure-1.jpg)\
Obrázek 1: Generace 0 a generace 1 GC.

Obrázek 2 ukazuje, že po `Obj1` generaci `Obj2` 2 GC, která viděla, že a jsou mrtvé, GC `Obj1` `Obj2`tvoří souvislé volné místo z `Obj4`paměti, které byly použity a , který pak byl použit k uspokojení požadavku na přidělení pro . Mezeru za posledním `Obj3`objektem , na konec segmentu lze také použít ke splnění požadavků na přidělení.

![Obrázek 2: Po gen 2 GC](media/loh/loh-figure-2.jpg)\
Obrázek 2: Po generaci 2 GC

Pokud není dostatek volného místa pro požadavky na přidělení velkých objektů, gc nejprve pokusí získat více segmentů z operačního prostoru. Pokud se to nepodaří, spustí generaci 2 GC v naději, že uvolní nějaký prostor.

Během generace 1 nebo generace 2 GC uvolňování uvolní segmenty, které nemají žádné živé objekty na ně zpět do operačního systému voláním [VirtualFree funkce](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Mezera za poslední živý objekt na konci segmentu je zrušena (s výjimkou dočasného segmentu, kde gen0/gen1 live, kde uvolňování paměti zachovat některé potvrzené, protože vaše aplikace bude přidělování v něm hned). A volné prostory zůstávají potvrzeny, i když jsou resetovány, což znamená, že operační systém nemusí zapisovat data do nich zpět na disk.

Vzhledem k tomu, že LOH se shromažďuje pouze během generace 2 GC, může být segment LOH uvolněn pouze během takového GC. Obrázek 3 znázorňuje scénář, kde uvolňování uvolní jeden segment (segment 2) zpět do operačního systému a zruší potvrzení více místa na zbývající segmenty. Pokud potřebuje použít zrušené místo na konci segmentu k uspokojení požadavků na přidělení velkých objektů, znovu potvrdí paměť. (Vysvětlení potvrzení/vyřazení naleznete v dokumentaci k [aplikaci VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Obrázek 3: LOH po gen 2 GC](media/loh/loh-figure-3.jpg)\
Obrázek 3: LOH po generaci 2 GC

## <a name="when-is-a-large-object-collected"></a>Kdy je velký objekt shromážděn?

Obecně platí, že GC dochází za jedné z následujících tří podmínek:

- Přidělení překračuje prahovou hodnotu generace 0 nebo velkého objektu.

  Prahová hodnota je vlastností generace. Prahová hodnota pro generaci je nastavena, když do ní systém uvolňování paměti přiděluje objekty. Při překročení prahové hodnoty gc je aktivována na tuto generaci. Při přidělování malé nebo velké objekty, spotřebovávají generace 0 a LOH prahové hodnoty, v uvedeném pořadí. Při uvolňování přiděluje do generace 1 a 2, spotřebovává jejich prahové hodnoty. Tyto prahové hodnoty jsou dynamicky vyladěny při spuštění programu.

  To je typický případ; většina řadičů domény dochází z důvodu přidělení na spravované haldy.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> je volána.

  Pokud je <xref:System.GC.Collect?displayProperty=nameWithType> volána metoda bez parametrů <xref:System.GC.MaxGeneration?displayProperty=nameWithType> nebo jiné přetížení je předán jako argument, LOH je shromažďována spolu se zbytkem spravované haldy.

- Systém je v situaci nedostatku paměti.

  K tomu dochází, když systém uvolňování paměti obdrží oznámení vysoké paměti z operačního systému. Pokud systém uvolňování paměti si myslí, že provedení generace 2 GC bude produktivní, aktivuje jeden.

## <a name="loh-performance-implications"></a>Důsledky výkonu LOH

Přidělení haldy velkého objektu ovlivňují výkon následujícími způsoby.

- Náklady na přidělení.

  CLR poskytuje záruku, že paměť pro každý nový objekt, který vydává, je vymazána. To znamená, že náklady na přidělení velkého objektu je zcela dominuje vymazání paměti (pokud se aktivuje GC). Pokud trvá 2 cykly vymazat jeden bajt, trvá 170 000 cyklů vymazat nejmenší velký objekt. Vymazání paměti objektu 16 MB v počítači s frekvencí 2 GHz trvá přibližně 16 ms. To je poměrně velká cena.

- Náklady na vyzvednutí.

  Vzhledem k tomu, že LOH a generace 2 jsou shromažďovány společně, pokud je překročena prahová hodnota jednoho z nich, je spuštěna kolekce generace 2. Pokud generace 2 kolekce se aktivuje z důvodu LOH, generace 2 nemusí být nutně mnohem menší po GC. Pokud není mnoho dat na generaci 2, to má minimální dopad. Ale pokud generace 2 je velký, může způsobit problémy s výkonem, pokud jsou spuštěny mnoho generace 2 GCs. Pokud mnoho velkých objektů jsou přiděleny na velmi dočasné bázi a máte velký SOH, můžete trávit příliš mnoho času dělá GCs. Kromě toho náklady na přidělení může opravdu sečíst, pokud budete mít přidělování a pustil opravdu velké objekty.

- Prvky pole s typy odkazů.

  Velmi velké objekty na LOH jsou obvykle pole (je velmi vzácné mít objekt instance, který je opravdu velký). Pokud prvky pole jsou bohaté na odkazy, vzniknou náklady, které nejsou k dispozici, pokud prvky nejsou bohaté na odkazy. Pokud prvek neobsahuje žádné odkazy, systém uvolňování paměti nemusí vůbec procházet polem. Pokud například použijete pole k ukládání uzlů v binárním stromu, jedním ze způsobů, jak jej implementovat, je odkazovat na pravý a levý uzel uzlu skutečnými uzly:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Pokud `num_nodes` je velký, uvolňování musí projít alespoň dva odkazy na prvek. Alternativním přístupem je uložení indexu pravého a levého uzlu:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Místo toho, aby odkazoval data levého uzlu jako `left.d` `binary_tr[left_index].d`, budete odkazovat na to jako . A uvolňování nemusí hledat žádné odkazy pro levý a pravý uzel.

Ze tří faktorů jsou první dva obvykle významnější než třetí. Z tohoto důvodu doporučujeme přidělit fond velkých objektů, které znovu použít namísto přidělování dočasných.

## <a name="collect-performance-data-for-the-loh"></a>Shromažďujte údaje o výkonu pro LOH

Před shromažďováním údajů o výkonu pro určitou oblast byste již měli provést následující kroky:

1. Našel jsem důkaz, že byste se měl podívat do této oblasti.

2. Vyčerpané další oblasti, které znáte, aniž byste našli něco, co by mohlo vysvětlit problém s výkonem, který jste viděli.

Podívejte se na blog [Pochopit problém, než se pokusíte najít řešení](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) pro další informace o základech paměti a cpu.

Ke shromažďování dat o výkonu LOH můžete použít následující nástroje:

- [Čítače výkonu paměti CLR rozhraní NET](#net-clr-memory-performance-counters)

- [Trasování událostí pro Windows – události](#etw-events)

- [Ladicí program](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Čítače výkonu paměti CLR rozhraní NET

Tyto čítače výkonu jsou obvykle dobrým prvním krokem při zkoumání problémů s výkonem (i když doporučujeme použít [události ETW](#etw-events)). Sledování výkonu nakonfigurujete přidáním požadovaných čítačů, jak ukazuje obrázek 4. Ty, které jsou relevantní pro LOH jsou:

- **Gen 2 Sbírky**

   Zobrazuje počet, kolikrát došlo ke vzniku 2 GOd od zahájení procesu. Čítač se zintáčí na konci kolekce generace 2 (také nazývá úplné uvolnění paměti). Tento čítač zobrazuje poslední pozorovanou hodnotu.

- **Velikost haldy velkých objektů**

   Zobrazí aktuální velikost loh v bajtech, včetně volného místa. Tento čítač je aktualizován na konci uvolňování paměti, nikoli při každém přidělení.

Běžný způsob, jak se podívat na čítače výkonu je s Sledování výkonu (perfmon.exe). Pomocí funkce Přidat čítače přidejte zajímavý čítač pro procesy, na kterých vám záleží. Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4:

![Snímek obrazovky s přidáním čítačů výkonu](media/large-object-heap/add-performance-counter.png)
Obrázek 4: LOH po generaci 2 GC

Čítače výkonu lze také dotazovat programově. Mnoho lidí je sbírat tímto způsobem jako součást jejich rutinní testování procesu. Když si všimnou čítačů s hodnotami, které jsou neobvyklé, používají jiné prostředky, aby získali podrobnější údaje, které pomáhají s vyšetřováním.

> [!NOTE]
> Doporučujeme použít události ETW namísto čítačů výkonu, protože ETW poskytuje mnohem bohatší informace.

### <a name="etw-events"></a>Trasování událostí pro Windows – události

Systém uvolňování paměti poskytuje bohatou sadu událostí ETW, které vám pomohou pochopit, co halda dělá a proč. Následující blogové příspěvky ukazují, jak shromažďovat a chápat události GC s ETW:

- [Gc ETW Události - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [Gc ETW Události - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [Gc ETW Události - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [Gc ETW Události - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Chcete-li identifikovat nadměrné generování 2 GCs způsobené dočasné přidělení LOH, podívejte se na aktivační důvod sloupec pro g. Pro jednoduchý test, který přiděluje pouze dočasné velké objekty, můžete shromažďovat informace o událostech ETW s následujícím příkazovým řádkem [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Výsledkem je něco jako toto:

![Snímek obrazovky, který zobrazuje události ETW v PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Obrázek 5: Události ETW zobrazené pomocí perfview

Jak můžete vidět, všechny gcs jsou generace 2 GC a všechny jsou spuštěny AllocLarge, což znamená, že přidělení velkého objektu spustilo tento GC. Víme, že tyto příděly jsou dočasné, protože **loh míra přežití %** sloupec říká, že 1%.

Můžete shromažďovat další události ETW, které vám řeknou, kdo tyto velké objekty přidělil. Následující příkazový řádek:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

shromažďuje AllocationTick událost, která je aktivována přibližně každý 100 kB v hodnotě přidělení. Jinými slovy událost je aktivována pokaždé, když je přidělen velký objekt. Pak se můžete podívat na jeden z gc haldy Alloc zobrazení, které ukazují volání zásobníky, které přiděleny velké objekty:

![Snímek obrazovky, který zobrazuje zobrazení haldy systému uvolňování paměti.](media/large-object-heap/garbage-collector-heap.png)
Obrázek 6: Zobrazení Alloc haldy GC

Jak můžete vidět, jedná se o velmi jednoduchý test, `Main` který právě přiděluje velké objekty z jeho metody.

### <a name="a-debugger"></a>Ladicí program

Pokud vše, co máte, je výpis stavu paměti a je třeba se podívat na jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladicího programu SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) poskytované rozhraním .NET.

> [!NOTE]
> Ladicí příkazy uvedené v této části jsou použitelné pro [ladicí program systému Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Následující ukazuje ukázkový výstup z analýzy LOH:

```console
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

Velikost haldy LOH je (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtů. Mezi adresami 023e1000 a 033db630, 8,008,736 bajtů <xref:System.Object?displayProperty=nameWithType> jsou obsazeny pole objektů, 6,663,696 <xref:System.Byte?displayProperty=nameWithType> bajtů jsou obsazeny pole objektů a 2,081,792 bajty jsou obsazeny volné místo.

V některých případech ladicí program ukazuje, že celková velikost LOH je menší než 85 000 bajtů. K tomu dochází, protože samotný runtime používá LOH přidělit některé objekty, které jsou menší než velký objekt.

Vzhledem k tomu, LOH není zhutněn, někdy LOH je myšlenka být zdrojem fragmentace. Fragmentací se rozumí:

- Fragmentace spravované haldy, která je označena množstvím volného místa mezi spravovanými objekty. V SoS `!dumpheap –type Free` příkaz zobrazí velikost volného místa mezi spravovanými objekty.

- Fragmentace adresního prostoru virtuální paměti (VM), `MEM_FREE`což je paměť označená jako . Můžete si ji pomocí různých ladicích příkazů v windbg.

   Následující příklad ukazuje fragmentaci v prostoru virtuálního montovana:

   ```console
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

Je běžnější zobrazit fragmentaci virtuálního trhu způsobenou dočasnými velkými objekty, které vyžadují, aby systém uvolňování paměti často získával nové segmenty spravované haldy z operačního systému a uvolnil prázdné zpět do operačního systému.

Chcete-li ověřit, zda LOH způsobuje fragmentaci virtuálního počítače, můžete nastavit zarážku na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) zobrazíte, kdo je volat. Chcete-li například zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážku takto:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Tento příkaz se rozdělí do ladicího programu a zobrazí zásobník volání pouze v [případě, že virtualalloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) je volána s velikostí přidělení větší než 8 MB (0x800000).

CLR 2.0 přidal funkci s názvem *Hromadění virtuálních počítačích,* která může být užitečná pro scénáře, kde jsou často získávány a vydávány segmenty (včetně velkých a malých objektů). Chcete-li zadat hromadění virtuálních montovny, zadejte příznak spuštění volaný `STARTUP_HOARD_GC_VM` prostřednictvím hostitelského rozhraní API. Místo uvolnění prázdné segmenty zpět do operačního systému, CLR zruší potvrzení paměti na tyto segmenty a umístí je do pohotovostního seznamu. (Všimněte si, že CLR neumožňuje pro segmenty, které jsou příliš velké.) CLR později používá tyto segmenty k uspokojení nových požadavků segmentu. Při příštím, že vaše aplikace potřebuje nový segment, CLR používá jeden z tohoto seznamu pohotovostního režimu, pokud může najít ten, který je dostatečně velký.

Hromadění virtuálních počítačů je také užitečné pro aplikace, které se chtějí držet segmenty, které již získaly, jako jsou některé serverové aplikace, které jsou dominantní aplikace spuštěné v systému, aby se zabránilo výjimkám z důvodu nedostatku paměti.

Důrazně doporučujeme, abyste pečlivě otestovali aplikaci při použití této funkce, abyste zajistili, že vaše aplikace má poměrně stabilní využití paměti.
