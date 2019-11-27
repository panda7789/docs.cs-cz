---
title: Základní informace o uvolňování paměti
description: Přečtěte si, jak systém uvolňování paměti funguje a jak je možné ho nakonfigurovat pro optimální výkon.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330420"
---
# <a name="fundamentals-of-garbage-collection"></a>Základní informace o uvolňování paměti

V modulu CLR (Common Language Runtime) slouží systém uvolňování paměti (GC) jako automatický správce paměti. Přináší následující výhody:

- Umožňuje vyvíjet aplikace bez nutnosti ručního uvolnění paměti.

- Přiděluje objekty na spravované haldě efektivně.

- Redeklarace objektů, které se již nepoužívají, vymaže jejich paměť a udržuje dostupnou paměť pro budoucí přidělení. Spravované objekty automaticky dostanou čistým obsahem, takže jejich konstruktory nemusí inicializovat každé datové pole.

- Zajišťuje bezpečnost paměti tím, že zajistí, že objekt nemůže použít obsah jiného objektu.

Tento článek popisuje základní koncepty uvolňování paměti.

## <a name="fundamentals-of-memory"></a>Základy paměti

Následující seznam shrnuje důležité koncepty paměti CLR.

- Každý proces má vlastní, oddělený virtuální adresní prostor. Všechny procesy ve stejném počítači sdílejí stejnou fyzickou paměť a stránkovací soubor, pokud je nějaký.

- Ve výchozím nastavení na 32 počítačích má každý proces virtuální adresní prostor 2 GB v uživatelském režimu.

- Jako vývojář aplikací pracujete jenom s virtuálním adresním prostorem a nikdy nepracujete s fyzickou pamětí přímo. Systém uvolňování paměti přiděluje a uvolňuje virtuální paměť na spravované haldě.

  Pokud píšete nativní kód, použijte funkce systému Windows pro práci s virtuálním adresním prostorem. Tyto funkce přidělují a uvolňují virtuální paměti pro vás na nativních haldách.

- Virtuální paměť může být ve třech stavech:

  - Dost. Blok paměti neobsahuje žádné odkazy a je k dispozici pro přidělení.

  - Rezervovaný. Blok paměti je k dispozici pro vaše použití a nelze jej použít pro žádnou jinou žádost o přidělení. Do tohoto bloku paměti však nelze ukládat data, dokud není potvrzeno.

  - Kterých. Blok paměti je přiřazený k fyzickému úložišti.

- Virtuální adresní prostor se může fragmentovat. To znamená, že v adresním prostoru jsou k dispozici bezplatné bloky, označované také jako díry. Po vyžádání přidělení virtuální paměti musí správce virtuální paměti najít jeden bezplatný blok, který je dostatečně velký pro splnění této žádosti o přidělení. I v případě, že máte 2 GB volného místa, přidělení, které vyžaduje 2 GB, bude neúspěšné, pokud všechny volné místo nejsou v jednom bloku adres.

- Pokud není k dispozici dostatek adresního prostoru pro rezervaci nebo fyzické místo pro potvrzení, můžete nedostatek paměti.

  Stránkovací soubor se používá i v případě, že je nízká tlak fyzické paměti (tj. poptávka pro fyzickou paměť). Když je první tlak fyzické paměti vysoký, operační systém musí uvolnit místo ve fyzické paměti pro ukládání dat a zálohuje některá data, která jsou ve fyzické paměti pro stránkovací soubor. Tato data nejsou stránkovaná, dokud je nepotřebujete, takže je možné vyskytnout stránkování v situacích, kdy je nízký tlak fyzické paměti.

## <a name="conditions-for-a-garbage-collection"></a>Podmínky pro uvolňování paměti

Uvolňování paměti nastane, pokud je splněna jedna z následujících podmínek:

- Systém má nedostatek fyzické paměti. Tato možnost je zjištěna buď pomocí oznámení o nedostatku paměti z operačního systému, nebo z nedostatku paměti, jak je uvedeno v hostiteli.

- Paměť, kterou používají přidělené objekty na spravované haldě, překročí přijatelnou prahovou hodnotu. Tato prahová hodnota je průběžně upravována při spuštění procesu.

- Je volána metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Ve většině případů není nutné volat tuto metodu, protože systém uvolňování paměti běží nepřetržitě. Tato metoda se primárně používá pro jedinečné situace a testování.

## <a name="the-managed-heap"></a>Spravovaná halda

Po inicializaci uvolňování paměti modulem CLR přidělí segment paměti pro ukládání a správu objektů. Tato paměť se nazývá spravovaná halda, nikoli nativní halda v operačním systému.

Pro každý spravovaný proces existuje spravovaná halda. Všechna vlákna v procesu přidělují paměť pro objekty ve stejné haldě.

Pro vyhradení paměti systém uvolňování paměti zavolá funkci Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a rezervuje pro spravované aplikace jeden segment paměti. Systém uvolňování paměti také vyhrazuje segmenty, jak je potřeba, a uvolní segmenty zpátky do operačního systému (po vymazání všech objektů) voláním funkce [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) systému Windows.

> [!IMPORTANT]
> Velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelných aktualizací. Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.

Čím méně objektů bylo přiděleno haldě, tím méně práce musí systém uvolňování paměti dělat. Při přidělování objektů nepoužívejte zaoblené hodnoty, které překračují vaše potřeby, jako je například přidělení pole 32 bajtů, pokud potřebujete pouze 15 bajtů.

Když je aktivováno uvolňování paměti, uvolňování paměti uvolní paměť, která je obsazena mrtvými objekty. Proces opětovného získání komprimuje živé objekty tak, aby se přesunuly dohromady, a nedoručené místo se odebere, takže halda bude menší. Tím zajistíte, aby objekty, které jsou přiděleny dohromady, zůstaly na spravované haldě, aby se zachovaly jejich místní chování.

Rušivost (četnost a doba trvání) uvolňování paměti je výsledkem objemu přidělení a množství zachované paměti na spravované haldě.

Halda může být považována za akumulaci dvou hald: [halda velkých objektů](large-object-heap.md) a haldy malých objektů.

[Halda velkých objektů](large-object-heap.md) obsahuje velmi velké objekty, které jsou 85 000 bajtů a větší. Objekty v haldě velkých objektů jsou obvykle pole. Je vzácná, že objekt instance bude velmi velký.

> [!TIP]
> Můžete [nakonfigurovat prahovou velikost](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pro objekty, které mají být v haldě velkých objektů.

## <a name="generations"></a>Všechna

Halda je uspořádána do generací, aby mohla zpracovávat dlouhodobé a krátkodobé nedlouhodobé objekty. K uvolňování paměti dochází hlavně v důsledku opětovného získávání krátkodobých objektů, které obvykle zabírají pouze malou část haldy. Existují tři generace objektů v haldě:

- **Generace 0**. Toto je nejmladšího sourozence generace a obsahuje krátkodobé objekty. Příkladem krátkodobého objektu je dočasná proměnná. K uvolňování paměti dochází nejčastěji v této generaci.

  Nově přidělené objekty tvoří novou generaci objektů a jsou implicitními kolekcemi 0. generace. Pokud se však jedná o velké objekty, přejdou na haldu velkých objektů v kolekci generace 2.

  Většina objektů je uvolněna pro uvolňování paměti v generaci 0 a nepředržela se do další generace.

- **Generace 1**. Tato generace obsahuje krátkodobé objekty a slouží jako vyrovnávací paměť mezi krátkodobé a dlouhodobé objekty.

- **Generace 2**. Tato generace obsahuje dlouhodobě nedlouhodobé objekty. Příkladem dlouhotrvajícího objektu je objekt v serverové aplikaci, který obsahuje statická data, která jsou po dobu trvání procesu aktivní.

K uvolňování paměti dochází na určitých generacích, protože podmínky zaručují. Shromáždění generace znamená shromažďování objektů v této generaci a všech jejích mladších generací. Uvolňování paměti 2. generace se označuje také jako úplné uvolňování paměti, protože přebírá všechny objekty ve všech generacích (tj. všechny objekty ve spravované haldě).

### <a name="survival-and-promotions"></a>Přežití a propagační akce

Objekty, které nejsou znovu získány v uvolňování paměti, jsou označovány jako zachované a jsou povýšeny na novou generaci. Objekty, které jsou zachovány uvolňováním paměti generace 0, jsou povýšeny na generaci 1; objekty, které jsou zachovány uvolňováním paměti generace 1, jsou povýšeny na generaci 2; a objekty, které jsou v procesu uvolňování paměti generace 2, zůstávají v generaci 2.

Když systém uvolňování paměti zjistí, že je míra přežití v generaci vysoká, zvyšuje se prahová hodnota přidělení pro tuto generaci. Další kolekce získá značnou velikost uvolněné paměti. CLR průběžně vyrovnává dvě priority: Pokud nechcete, aby pracovní sada aplikace byla příliš velká, pomocí opožděného uvolňování paměti a neumožnilo spouštění uvolňování paměti příliš často.

### <a name="ephemeral-generations-and-segments"></a>Dočasné generace a segmenty

Vzhledem k tomu, že objekty v generacích 0 a 1 jsou krátkodobé, tyto generace jsou známy jako dočasné generace.

Dočasné generace musí být přiděleny v segmentu paměti, který je znám jako dočasný segment. Každý nový segment získaný systémem uvolňování paměti se stal novým dočasným segmentem a obsahuje objekty, které předržely uvolňování paměti generace 0. Starý dočasný segment se vytvoří jako nový segment 2. generace.

Velikost dočasného segmentu se liší v závislosti na tom, zda je systém 32 nebo 64 a na typu uvolňování paměti, které je spuštěn. Výchozí hodnoty jsou uvedeny v následující tabulce.

||32bitový|64bitový|
|-|-------------|-------------|
|GC pracovní stanice|16 MB|256 MB|
|Uvolňování paměti serveru|64 MB|4 GB|
|GC serveru s logickými procesory > 4|32 MB|2 GB|
|Uvolňování paměti serveru s využitím > 8 logických procesorů|16 MB|1 GB|

Dočasný segment může zahrnovat objekty generace 2. Objekty generace 2 můžou používat víc segmentů (tolik, kolik je váš proces vyžaduje, a paměť umožňuje).

Velikost volné paměti z dočasného uvolňování paměti je omezená na velikost dočasného segmentu. Velikost paměti, která je uvolněna, je úměrná místu, které byly obsazeny neaktivními objekty.

## <a name="what-happens-during-a-garbage-collection"></a>Co se stane během uvolňování paměti

Uvolňování paměti má následující fáze:

- Fáze označení, která najde a vytvoří seznam všech živých objektů.

- Fáze přemístění, která aktualizuje odkazy na objekty, které budou zkomprimovány.

- Kompaktní fáze, která uvolňuje místo obsazené neaktivními objekty a komprimuje zbývající objekty. Fáze komprimace přesune objekty, které předržely uvolňování paměti směrem na starší konec segmentu.

  Vzhledem k tomu, že kolekce 2. generace mohou zabírat více segmentů, objekty, které jsou povýšeny do generace 2, lze přesunout do staršího segmentu. Generace 1 i 2, zachované, je možné přesunout do jiného segmentu, protože jsou povýšeny na generaci 2.

  Obvykle se nekomprimuje halda pro velké objekty (LOH), protože kopírování velkých objektů ukládá snížení výkonu. V rozhraní .NET Core a v .NET Framework 4.5.1 a novějších verzích ale můžete použít vlastnost <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> k komprimaci haldy velkých objektů na vyžádání. Kromě toho se LOH automaticky zkomprimuje, když se nastaví pevný limit zadáním těchto znaků:

  - omezení paměti na kontejneru, nebo
  - [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) nebo [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) možnosti konfigurace modulu runtime

Systém uvolňování paměti používá následující informace k určení, zda jsou objekty živé:

- **Kořeny zásobníku**. Proměnné zásobníku poskytované kompilátorem JIT (just-in-time) a zásobníkem Stack prohlížeč. Optimalizace JIT mohou prodloužit nebo zkrátit oblasti kódu, ve kterých jsou proměnné zásobníku hlášeny do uvolňování paměti.

- **Popisovače uvolňování paměti**. Obslužné rutiny, které odkazují na spravované objekty a které mohou být přiděleny uživatelským kódem nebo modulem CLR (Common Language Runtime).

- **Statická data**. Statické objekty v aplikačních doménách, které by mohly odkazovat na jiné objekty. Každá doména aplikace udržuje přehled o svých statických objektech.

Před spuštěním uvolňování paměti jsou všechna spravovaná vlákna pozastavena s výjimkou vlákna, které vyvolalo uvolňování paměti.

Následující ilustrace znázorňuje vlákno, které spouští uvolňování paměti a způsobuje pozastavení ostatních vláken.

![Když vlákno spustí uvolňování paměti](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulace s nespravovanými prostředky

Pokud spravované objekty odkazují na nespravované objekty pomocí jejich nativních popisovačů souborů, je nutné explicitně uvolnit nespravované objekty, protože systém uvolňování paměti pouze sleduje paměť na spravované haldě.

Uživatelé spravovaného objektu nemohou uvolnit nativní prostředky používané objektem. K provedení vyčištění můžete nastavit, aby se spravovaný objekt mohl dokončit. Finalizace se skládá z akcí čištění, které se spustí, když se objekt již nepoužívá. Když spravovaný objekt zemře, provede čisticí akce, které jsou určeny v jeho metodě finalizační metody.

Když je zjištěna nekonečná činnost objektu, je jeho finalizační metoda vložena do fronty, aby byly provedeny jeho akce čištění, ale samotný objekt je povýšen na novou generaci. Proto musíte počkat až do dalšího uvolňování paměti, ke kterému dojde v této generaci (což není nutně další uvolňování paměti), abyste zjistili, zda byl objekt uvolněn.

Další informace o finalizaci najdete v tématu <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Uvolnění paměti pracovní stanice a serveru

Systém uvolňování paměti je samoobslužné ladění a může fungovat v nejrůznějších scénářích. Pomocí [nastavení konfiguračního souboru](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) můžete nastavit typ uvolňování paměti na základě charakteristik zatížení. CLR poskytuje následující typy uvolňování paměti:

- Uvolňování paměti pracovních stanic (GC) je navrženo pro klientské aplikace. Pro samostatné aplikace je výchozím charakterem GC. U hostovaných aplikací, například těch, které hostuje ASP.NET, hostitel určí výchozí charakter GC.

  Uvolňování paměti pracovní stanice může být souběžné nebo nesouběžné. Souběžné uvolňování paměti umožňuje spravovaným vláknům pokračovat v operacích během uvolňování paměti. [Kolekce uvolnění paměti na pozadí](#background-workstation-garbage-collection) nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) v .NET Framework 4 a novějších verzích.

- Uvolňování paměti serveru, které je určeno pro serverové aplikace, které vyžadují vysokou propustnost a škálovatelnost.

  - V rozhraní .NET Core může být uvolňování paměti serveru nesouběžné nebo na pozadí.

  - V .NET Framework 4,5 a novějších verzích může být uvolňování paměti serveru nesouběžné nebo pozadí (pro shromažďování paměti na pozadí nahrazuje souběžné uvolňování paměti). V .NET Framework 4 a předchozích verzích je uvolňování paměti serveru nesouběžné.

Následující ilustrace znázorňuje vyhrazená vlákna, která provádějí uvolňování paměti na serveru:

![Vlákna uvolňování paměti serveru](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Porovnání shromažďování paměti pracovní stanice a serveru

Následují požadavky na vlákna a výkon pro uvolňování paměti pracovních stanic:

- Kolekce probíhá na uživatelském vlákně, které aktivovalo uvolňování paměti a zůstává ve stejné prioritě. Vzhledem k tomu, že se uživatelské vlákna obvykle spouští s normální prioritou, musí být systém uvolňování paměti (který běží na normální prioritní vlákně) s ostatními vlákny pro čas procesoru. (Vlákna, která spouštějí nativní kód, nejsou pozastavena buď na serveru, nebo v uvolnění paměti pracovní stanice.)

- Uvolňování paměti pracovní stanice se vždycky používá v počítači, který má jenom jeden procesor, bez ohledu na [nastavení konfigurace](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Následují požadavky na vlákna a výkon pro uvolňování paměti serveru:

- Kolekce probíhá na několika vyhrazených vláknech, které jsou spuštěny na úrovni priority `THREAD_PRIORITY_HIGHEST`.

- Halda a vyhrazené vlákno pro provádění uvolňování paměti jsou k dispozici pro každý procesor a haldy jsou shromažďovány ve stejnou dobu. Každá halda obsahuje malou haldu objektů a velké haldy objektů a ke všem haldám je možné přistupovat pomocí uživatelského kódu. Objekty na různých haldách mohou vzájemně odkazovat.

- Vzhledem k tomu, že více vláken uvolňování paměti současně spolupracuje, je uvolňování paměti serveru rychlejší než uvolnění paměti pracovní stanice ve stejné velikosti haldy.

- Uvolňování paměti serveru má často větší velikost segmentů. Toto je však pouze generalizace: velikost segmentu je specifická pro konkrétní implementaci a může se změnit. Při ladění aplikace nevytvářejte předpoklady o velikosti segmentů přidělených systémem uvolňování paměti.

- Uvolňování paměti serveru může být náročné na prostředky. Představte si například, že v počítači, který má 4 procesory, je spuštěno 12 procesů, které používají GC serveru. Pokud se u všech procesů vyskytne uvolňování paměti ve stejnou dobu, může to narušit navzájem, protože ve stejném procesoru bylo naplánováno 12 vláken. Pokud jsou procesy aktivní, není vhodné, abyste je používali při použití GC serveru.

Pokud používáte stovky instancí aplikace, zvažte použití uvolňování paměti pracovní stanice se zakázaným souběžným uvolňováním paměti. Výsledkem bude méně přepínání kontextu, což může zlepšit výkon.

## <a name="background-workstation-garbage-collection"></a>Uvolňování paměti pracovní stanice na pozadí

V případě uvolnění paměti pracovní stanice na pozadí jsou dočasné generace (0 a 1) shromažďovány podle potřeby, zatímco probíhá shromažďování 2. generace. Uvolňování paměti pracovní stanice na pozadí se provádí ve vyhrazeném vlákně a vztahuje se pouze na kolekce 2. generace.

Uvolňování paměti na pozadí je ve výchozím nastavení povolené a dá se zapnout nebo vypnout v nastavení konfigurace [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) v aplikacích .NET Framework nebo v nastavení [System. GC. souběžné](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) v aplikacích .NET Core.

> [!NOTE]
> Uvolňování paměti na pozadí nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) a je k dispozici v .NET Framework 4 a novějších verzích. V .NET Framework 4 se podporuje jenom pro uvolňování paměti pracovní stanice. Počínaje .NET Framework 4,5 se uvolňování paměti na pozadí dá použít jak pro pracovní stanice, tak pro uvolňování paměti serveru.

Kolekce na dočasných generacích během uvolňování paměti na pozadí je známá jako uvolnění paměti na popředí. Když dojde k uvolnění paměti na popředí, pozastaví se všechna spravovaná vlákna.

Když probíhá uvolňování paměti na pozadí a přidělíte dostatek objektů v generaci 0, modul CLR provede uvolňování paměti od generace 0 nebo 1. generace v popředí. Vyhrazené vlákno uvolňování paměti na pozadí kontroluje v častých bezpečných bodech, aby bylo možné zjistit, zda existuje požadavek na uvolnění paměti na popředí. V takovém případě se kolekce na pozadí odblokuje, aby mohlo dojít k uvolnění paměti na popředí. Po dokončení uvolňování paměti na popředí se obnoví vyhrazené vlákno kolekce uvolnění paměti na pozadí a uživatelské vlákna.

Uvolňování paměti na pozadí odebírá omezení přidělení, která jsou vynucená souběžným uvolňováním paměti, protože dočasné uvolňování paměti mohou nastat během uvolňování paměti na pozadí. Uvolňování paměti na pozadí může odebrat nedoručené objekty v dočasných generacích. Může také rozšířit haldu v případě potřeby během uvolňování paměti 1. generace.

Následující obrázek znázorňuje pozadí uvolňování paměti prováděné na samostatném vyhrazeném vlákně pracovní stanice:

![Uvolňování paměti pracovní stanice na pozadí](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Uvolňování paměti serveru na pozadí

Počínaje .NET Framework 4,5 je uvolňování paměti serveru na pozadí výchozím režimem pro uvolňování paměti serveru.

Uvolňování paměti serveru na pozadí funguje podobně jako uvolnění paměti pracovní stanice na pozadí, které je popsané v předchozí části, ale existuje několik rozdílů:

- Uvolňování paměti pracovní stanice na pozadí používá jedno vyhrazené vlákno uvolňování paměti na pozadí, zatímco uvolňování paměti serveru na pozadí používá více vláken. Obvykle existuje vyhrazené vlákno pro každý logický procesor.

- Na rozdíl od vlákna uvolňování paměti na pozadí pracovní stanice nevypršel časový limit těchto vláken.

Následující obrázek znázorňuje pozadí uvolňování paměti prováděné na samostatném vyhrazeném vlákně na serveru:

![Uvolňování paměti serveru na pozadí](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti

> [!TIP]
> Tato část se týká:
>
> - Uvolňování paměti pro pracovní stanice .NET Framework 3,5 a starší
> - .NET Framework 4 a starší pro uvolňování paměti serveru
>
> Souběžné uvolňování paměti je nahrazeno [uvolňováním paměti na pozadí](#background-workstation-garbage-collection) v novějších verzích.

V pracovní stanici nebo uvolňování paměti serveru můžete [Povolit souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), které umožňuje spouštět vlákna souběžně s vyhrazeným vláknem, které provádí uvolňování paměti po většinu doby trvání kolekce. Tato možnost má vliv jenom na uvolňování paměti v generaci 2. generace 0 a 1 jsou vždy nesouběžná, protože dokončí velmi rychle.

Souběžné uvolňování paměti umožňuje interaktivním aplikacím lépe reagovat tím, že minimalizuje pozastavení kolekce. Spravovaná vlákna mohou i nadále běžet v době, kdy běží souběžné vlákno uvolňování paměti. Výsledkem je kratší pozastavení během uvolňování paměti.

Souběžné uvolňování paměti se provádí ve vyhrazeném vlákně. Ve výchozím nastavení spustí modul CLR uvolnění paměti pracovní stanice s povoleným souběžným uvolňováním paměti. To platí pro počítače s jedním procesorem a více procesory.

Následující ilustrace znázorňuje souběžné uvolňování paměti prováděné na samostatném vyhrazeném vlákně.

![Souběžná vlákna uvolňování paměti](./media/gc-concurrent.png)

## <a name="see-also"></a>Viz také:

- [Možnosti konfigurace pro GC](../../core/run-time-config/garbage-collector.md)
- [Uvolňování paměti](index.md)
