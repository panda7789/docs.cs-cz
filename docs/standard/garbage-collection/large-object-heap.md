---
title: Halda velkých objektů v systémech Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4663c42b784334f66318c61d531ab4cee2f8b02e
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71354053"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Halda velkých objektů v systémech Windows

Uvolňování paměti .NET (GC) rozděluje objekty až do malých a velkých objektů. Když je objekt rozsáhlý, některé z jeho atributů se stanou důležitější, než když je objekt malý. Například jeho komprimací – to znamená, že je třeba ho zkopírovat do paměti jinde na haldě – může být nákladné. Z tohoto důvodu systém uvolňování paměti .NET umístí velké objekty na haldu velkých objektů (LOH). V tomto tématu se podrobněji podíváme na haldu velkých objektů. Probereme, co tento objekt jako velký má, jak se shromažďují tyto velké objekty a jaký druh vlivu na výkon mají velké objekty.

> [!IMPORTANT]
> Toto téma popisuje haldu velkých objektů v .NET Framework a .NET Core, které běží pouze na systémech Windows. Nepokrývá LOH běžící na implementacích .NET na jiných platformách.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak objekt skončí na haldě velkých objektů a jak je v GC zpracovává

Pokud je objekt větší nebo roven 85 000 bajtů, je považován za velký objekt. Toto číslo bylo určeno vyladěním výkonu. Pokud je požadavek na přidělení objektu na 85 000 nebo více bajtů, modul runtime ho přidělí na haldu velkých objektů.

Pro pochopení toho, co to znamená, je vhodné si prostudovat některé zásadní informace o modulu .NET GC.

Uvolňování paměti .NET je kolekce. Má tři generace: generace 0, generace 1 a generace 2. Důvodem pro 3 generace je to, že v dobře vyladěné aplikaci většina objektů v gen0. Například v serverové aplikaci musí být přidělení přidružená ke každé žádosti po dokončení žádosti kostka. Požadavky na přidělení v letadle provedou Gen1 a Die. Gen1 v podstatě funguje jako vyrovnávací paměť mezi mladými oblastmi objektů a dlouhodobými oblastmi objektů.

Malé objekty jsou vždy přiděleny v generaci 0 a v závislosti na jejich životnosti mohou být povýšeny na generaci 1 nebo generation2. Velké objekty jsou vždy přiděleny v generaci 2.

Velké objekty patří do generace 2, protože jsou shromažďovány pouze během kolekce generace 2. Po shromáždění generace se shromažďují také všechny jeho mladší generace. Například když dojde k 1. generaci GC, shromažďují se obě generace 1 a 0. A když dojde k GC generace 2, bude shromážděna celá halda. Z tohoto důvodu se také označuje jako *úplný GC*. generace 2 GC. Tento článek odkazuje na generaci 2 GC místo úplného uvolňování paměti, ale tyto výrazy jsou zaměnitelné.

Generace poskytují logické zobrazení haldy GC. Fyzicky objekty ve spravovaných segmentech haldy jsou živé. *Segment spravované haldy* je blok paměti, který GC vyhradí z operačního systému voláním [funkce VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jménem spravovaného kódu. Když je modul CLR načten, uvolňování paměti přidělí dva počáteční segmenty haldy: jeden pro malé objekty (halda malých objektů nebo SOH) a jeden pro velké objekty (Large Object halda).

Žádosti o přidělení se pak splní vložením spravovaných objektů na tyto spravované segmenty haldy. Pokud je objekt menší než 85 000 bajtů, je umístěn do segmentu pro SOH; v opačném případě je umístěn na segment LOH. Segmenty jsou potvrzeny (v menších blocích), protože jsou jim přiděleny další a více objektů.
Pro SOH jsou objekty, které jsou v GC, povýšeny na novou generaci. Objekty, které jsou zachovány kolekcí 0. generace, se nyní považují za objekty generace 1 a tak dále. Nicméně objekty, které zůstávají nejstarší generace, jsou stále považovány za nejstarší generace. Jinými slovy, pozůstaly od generace 2 objekty generace 2; a zbývající objekty z LOH jsou objekty LOH (které jsou shromažďovány pomocí Gen2).

Uživatelský kód může přidělit pouze v generaci 0 (malé objekty) nebo LOH (velké objekty). Pouze GC může "přidělit" objekty v generaci 1 (zvýšením úrovně pozůstalcích od generace 0) a generace 2 (zvýšením úrovně podržených z generací 1 a 2).

Když je aktivováno uvolňování paměti, GC provede trasování v rámci živých objektů a zkomprimuje je. Ale vzhledem k tomu, že komprimace je nákladné *, uvolňování* paměti LOH; Vytvoří volný seznam z neaktivních objektů, které lze později znovu použít k uspokojení požadavků na přidělení velkých objektů. Sousední nedoručené objekty jsou vytvořeny do jednoho volného objektu.

.NET Core a .NET Framework (počínaje .NET Framework 4.5.1) obsahují <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> vlastnost, která umožňuje uživatelům určit, že by měl být LOH při příštím úplném blokování GC. A v budoucnu se může .NET rozhodnout LOH automaticky zkomprimovat. To znamená, že pokud přidělíte velké objekty a chcete zajistit, aby se nepřesunuly, měli byste je stále připnout.

Obrázek 1 znázorňuje situaci, kdy se generace GC vydává 1 po první generaci 0 °c, `Obj1` kde `Obj3` a jsou neaktivní, a generace formulářů 2 po prvním 1. generaci GC, `Obj2` kde `Obj5` a jsou neaktivní. Všimněte si, že tato a následující čísla jsou pouze pro ilustrační účely; obsahují velmi málo objektů, aby lépe ukázaly, co se děje na haldě. Ve skutečnosti je mnoho dalších objektů obvykle součástí GC.

![Obrázek 1: GC s globálním 0 a GC 1. generace](media/loh/loh-figure-1.jpg)\
Obrázek 1: Generace 0 a 1. generace GC.

Na obrázku 2 se dozvíte, že po 2. generaci `Obj1` GC `Obj2` , který se zjistil, že a jsou neaktivní, tvoří GC volné místo z paměti, která se `Obj1` používá `Obj2`k tomu, aby využívala a, která se pak použila k uspokojení žádosti o přidělení. pro `Obj4`. Místo za posledním objektem,, `Obj3`do konce segmentu, lze také použít k uspokojení požadavků na přidělení.

![Obrázek 2: Po 1. generace GC](media/loh/loh-figure-2.jpg)\
Obrázek 2: Po 2. generaci GC

Pokud není dostatek volného místa pro uspokojení požadavků na přidělení velkých objektů, GC se nejprve pokusí získat další segmenty z operačního systému. Pokud se to nepodaří, aktivuje se GC generace 2 v průběhu uvolnění místa.

Během generace 1 nebo generace 2 GC uvolňuje segmenty uvolňování paměti, které nemají žádné živé objekty, zpět do operačního systému voláním [funkce VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Místo za posledním živým objektem na konci segmentu je depotvrzeno (s výjimkou dočasného segmentu, kde gen0/Gen1 Live, kde systém uvolňování paměti uchovává nějaké potvrzené, protože vaše aplikace se hned přiděluje). A volná místa zůstávají i po resetování, což znamená, že operační systém nemusí zapisovat data do disku zpět na disk.

Vzhledem k tomu, že je LOH shromážděna pouze během generace 2 GC, segment LOH může být uvolněn pouze během takového GC. Obrázek 3 znázorňuje scénář, ve kterém uvolňování paměti uvolní jeden segment (segment 2) zpátky na operační systém a ve zbývajících segmentech zruší více místa. Pokud musí použít odstraněné místo na konci segmentu, aby se splnily požadavky na velké nároky na přidělení objektů, pak se znovu potvrdí. (Vysvětlení potvrzení/zrušení potvrzení naleznete v dokumentaci k [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Obrázek 3: LOH po 1. generace GC](media/loh/loh-figure-3.jpg)\
Obrázek 3: LOH po generaci 2 GC

## <a name="when-is-a-large-object-collected"></a>Kdy je shromážděn velký objekt?

Obecně platí, že k GC dojde, když dojde k jedné z následujících 3 podmínek:

- Přidělení překračuje prahovou hodnotu pro generaci 0 nebo velký objekt.

  Prahová hodnota je vlastnost generace. Prahová hodnota pro generování je nastavena, když systém uvolňování paměti přiděluje objekty do objektu. Při překročení prahové hodnoty se v této generaci aktivuje GC. Při přidělování malých nebo velkých objektů spotřebováváte generace 0 a prahové hodnoty LOH v uvedeném pořadí. Když systém uvolňování paměti přidělí do generace 1 a 2, spotřebuje jejich prahové hodnoty. Tyto prahové hodnoty jsou dynamicky vyladěny při spuštění programu.

  Toto je obvyklý případ. k většině GC dochází z důvodu přidělení na spravované haldě.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda je volána.

  Pokud je volána <xref:System.GC.Collect?displayProperty=nameWithType> metoda bez parametrů nebo je jako argument předána <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jiná přetížená metoda, je LOH shromážděn spolu se zbytkem spravované haldy.

- Systém je ve stavu nedostatku paměti.

  K tomu dochází, když systém uvolňování paměti obdrží oznámení o vysoké paměti z operačního systému. Pokud systém uvolňování paměti předpokládá, že se v GC generace 2 zvýší produktivita, spustí se jedna.

## <a name="loh-performance-implications"></a>Důsledky výkonu LOH

Alokace u haldy velkých objektů má vliv na výkon následujícími způsoby.

- Náklady na přidělení.

  CLR zajišťuje záruku toho, že paměť pro každý nový objekt, který je vykazuje, je vymazána. To znamená, že náklady na přidělení velkého objektu jsou zcela ovládány vymazáním paměti (Pokud se nespustí GC). Pokud potrvá dva cykly k vymazání jednoho bajtu, bude trvat 170 000 cyklů, aby se vymazal nejmenší velký objekt. Vymazání paměti objektu 16MB na 2GHz počítači trvá přibližně 16MS. To je spíše velké náklady.

- Náklady na shromažďování.

  Vzhledem k tomu, že jsou LOH a generace 2 shromažďovány společně, pokud je překročena prahová hodnota jedné z nich, je aktivována kolekce 2. generace. Pokud je kolekce generace 2 aktivována z důvodu LOH, generace 2 nebude nutně po GC mnohem menší. Pokud pro generaci 2 není k dispozici žádné množství dat, má minimální dopad. Pokud je ale generace 2 Velká, může to způsobit problémy s výkonem, pokud se spustí spousta generace 2 GC. Pokud je mnoho velkých objektů přiděleno velmi dočasnému základu a máte velký počet SOH, může být útrata příliš mnoho času GC. Kromě toho mohou být náklady na přidělení skutečně přidány, pokud budete přiřazovat a vracet ve skutečnosti velké objekty.

- Prvky pole s odkazovým typem.

  Velmi velké objekty v LOH jsou obvykle pole (velmi zřídka mají objekt instance, který je ve skutečnosti velký). Pokud jsou prvky pole na úrovni reference, dojde k nepřítomnosti nákladů, které nejsou k dispozici, pokud prvky nejsou na přehledně formátované. Pokud element neobsahuje žádné odkazy, systém uvolňování paměti nemusí projít všemi poli. Například pokud použijete pole k ukládání uzlů v binárním stromu, jedním ze způsobů, jak ho implementovat, je odkazování na pravý a levý uzel uzlu skutečnými uzly:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Pokud `num_nodes` je velká, musí systém uvolňování paměti projít alespoň dvěma odkazy na jeden prvek. Alternativním přístupem je uložit index pravého a levého uzlu:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Místo odkazování na data `left.d`levého uzlu se na něj odkazuje jako `binary_tr[left_index].d`na. A systém uvolňování paměti nemusí pohlížet na žádné odkazy pro levý a pravý uzel.

Z těchto tří faktorů jsou první dva většinou mnohem významné než třetí. Z tohoto důvodu doporučujeme, abyste přidělili fond velkých objektů, které znovu použijete místo přidělení dočasných.

## <a name="collecting-performance-data-for-the-loh"></a>Shromažďování údajů o výkonu pro LOH

Předtím, než shromáždíte údaje o výkonu konkrétní oblasti, byste už měli provést následující:

1. Bylo nalezeno legitimace, které byste měli v této oblasti prohledat.

2. Byly vyčerpány jiné oblasti, o kterých víte, že nenajdete cokoli, co by mohlo vysvětlit problém s výkonem, který jste viděli.

[Než se pokusíte najít řešení](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) , kde najdete další informace o základech paměti a procesoru, podívejte se na blog.

K shromažďování dat o výkonu LOH můžete použít následující nástroje:

- [Čítače výkonu paměti .NET CLR](#net-clr-memory-performance-counters)

- [Události ETW](#etw-events)

- [Ladicí program](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Čítače výkonu paměti .NET CLR

Tyto čítače výkonu jsou obvykle dobrým prvním krokem při zkoumání problémů s výkonem (i když doporučujeme použít [události ETW](#etw-events)). Nástroj Sledování výkonu konfigurujete tak, že přidáte čítače, které chcete, jak ukazuje obrázek 4. Ty, které jsou relevantní pro LOH, jsou:

- **Kolekce 2. generace**

   Zobrazuje počet, kolikrát od spuštění procesu došlo k GC 2. generace. Čítač se zvyšuje na konci kolekce 2. generace (označuje se také jako úplné uvolňování paměti). Tento čítač zobrazuje poslední zjištěnou hodnotu.

- **Velikost haldy Large Object**

   Zobrazí aktuální velikost LOH v bajtech, včetně volného místa. Tento čítač se aktualizuje na konci uvolňování paměti, ne při každém přidělení.

Běžný způsob, jak si prohlédnout čítače výkonu, je nástroj Performance Monitor (Perfmon. exe). Pomocí možnosti Přidat čítače přidejte zajímavé čítače pro procesy, které vás zajímají. Data čítače výkonu můžete uložit do souboru protokolu, jak ukazuje obrázek 4:

![Screenshow, která ukazuje přidání čítačů výkonu.](media/large-object-heap/add-performance-counter.png)
Obrázek 4: LOH po generaci 2 GC

Čítače výkonu se také dají dotazovat programově. Spousta lidí je shromažďuje tímto způsobem v rámci procesu pravidelného testování. Když vydávají čítače s hodnotami, které jsou z obyčejného, používají jiné prostředky k získání podrobnějších dat, která vám pomohou s šetřením.

> [!NOTE]
> Doporučujeme místo čítačů výkonu použít události trasování událostí pro Windows, protože trasování událostí pro Windows poskytuje mnohem rozsáhlejší informace.

### <a name="etw-events"></a>Trasování událostí pro Windows – události

Systém uvolňování paměti poskytuje bohatou sadu událostí ETW, které vám pomůžou pochopit, co dělá halda a proč. Následující blogové příspěvky ukazují, jak shromažďovat a pochopit události GC pomocí ETW:

- [GC – události ETW – 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [GC – události ETW – 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [GC – události ETW – 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [GC – události ETW – 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Chcete-li identifikovat nadměrné GC 2. generace způsobené dočasným přidělením LOH, podívejte se do sloupce důvod triggeru pro GC. Pro jednoduchý test, který přiděluje pouze dočasné velké objekty, můžete shromažďovat informace o událostech ETW pomocí následujícího příkazového řádku [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) :

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Výsledek je podobný tomuto:

![Snímek obrazovky, který zobrazuje události ETW v PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Obrázek 5: Události ETW zobrazené pomocí PerfView

Jak vidíte, všechny GC jsou generace 2 GC a všechny jsou spouštěny v AllocLarge, což znamená, že přidělením velkého objektu aktivovaného tímto GC. Víme, že tato přidělení jsou dočasná, protože **sazba LOH pro přežití%** kolony uvádí 1%.

Můžete shromažďovat další události ETW, které vám sdělí, kdo tyto velké objekty přidělil. Následující příkazový řádek:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

shromažďuje událost AllocationTick, která se aktivuje přibližně pro každé 100 tisíc množství přidělení. Jinými slovy, událost je vyvolána při každém přidělení velkého objektu. Pak se můžete podívat na jedno z zobrazení přidělení haldy GC, které vám ukáže zásobníky voláníi, že se přidělily velké objekty:

![Snímek obrazovky zobrazující zobrazení haldy systému uvolňování paměti.](media/large-object-heap/garbage-collector-heap.png)
Obrázek 6: Zobrazení přidělení haldy GC

Jak vidíte, jedná se o velmi jednoduchý test, který pouze přiděluje velké objekty od své `Main` metody.

### <a name="a-debugger"></a>Ladicí program

Pokud je to výpis paměti a potřebujete zjistit, jaké objekty jsou ve skutečnosti na LOH, můžete použít [rozšíření ladicího programu SOS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) , které poskytuje .NET.

> [!NOTE]
> Příkazy ladění uvedené v této části platí pro [ladicí programy systému Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Následující ukázka ukazuje výstup z analýzy LOH:

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

Velikost haldy LOH je (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtů. Mezi adresami 023e1000 a 033db630, 8 008 736 bajtů, které jsou obsazeny polem <xref:System.Object?displayProperty=nameWithType> objektů, 6 663 696 bajty jsou obsazeny <xref:System.Byte?displayProperty=nameWithType> polem objektů a 2 081 792 bajtů je obsazeno volným místem.

V některých případech ladicí program zobrazí, že celková velikost LOH je menší než 85 000 bajtů. K tomu dochází, protože modul runtime sám používá LOH k přidělení některých objektů, které jsou menší než velký objekt.

Vzhledem k tomu, že se LOH nekomprimuje, někdy se LOH považuje za zdroj fragmentace. Fragmentace znamená:

- Fragmentace spravované haldy, která je určena množstvím volného místa mezi spravovanými objekty. V SOS `!dumpheap –type Free` příkaz zobrazí množství volného místa mezi spravovanými objekty.

- Fragmentace adresního prostoru virtuální paměti (VM), což je paměť označená jako `MEM_FREE`. Můžete ji získat pomocí různých příkazů ladicího programu v programu WinDbg.

   Následující příklad ukazuje fragmentaci v prostoru virtuálního počítače:

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

Je častěji vidět, že fragmentace virtuálního počítače je způsobená dočasnými velkými objekty, které vyžadují, aby systém uvolňování paměti často získal nové spravované segmenty haldy z operačního systému a uvolnil prázdné hodnoty zpátky do operačního systému.

Chcete-li ověřit, zda LOH způsobuje fragmentaci virtuálního počítače, můžete nastavit zarážku na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) , aby bylo možné zjistit, kdo je volá. Například chcete-li zjistit, kdo se pokusil přidělit bloky virtuální paměti větší než 8MBB z operačního systému, můžete nastavit zarážku takto:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Tento příkaz se přeruší do ladicího programu a zobrazí zásobník volání pouze v případě, že je metoda [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) volána s velikostí alokace větší než 8MB (0x800000).

CLR 2,0 přidal funkci s názvem *VM hoarding* , která může být užitečná pro scénáře, kdy se často získávají a uvolňují segmenty (včetně v haldách velkých a malých objektů). Pokud chcete zadat hoarding virtuálního počítače, zadejte spouštěcí příznak nazvaný `STARTUP_HOARD_GC_VM` prostřednictvím hostujícího rozhraní API. Místo uvolnění prázdných segmentů zpět do operačního systému modul CLR zruší v těchto segmentech paměť a umístí je do úsporného seznamu. (Všimněte si, že modul CLR to neudělá pro segmenty, které jsou příliš velké.) Modul CLR později použije tyto segmenty k uspokojení požadavků na nové segmenty. Až aplikace příště potřebuje nový segment, použije modul CLR jeden z těchto seznamů v pohotovostním režimu, pokud může najít dostatečně velký.

Hoarding virtuálního počítače je také užitečné pro aplikace, které chcete umístit na segmenty, které již získali, například některé serverové aplikace, které jsou dominantní aplikace spuštěné v systému, aby nedocházelo k výjimkám výjimek paměti.

Důrazně doporučujeme, abyste aplikaci pečlivě otestovali při použití této funkce, abyste zajistili, že má vaše aplikace poměrně stabilní využití paměti.
