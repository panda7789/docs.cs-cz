---
title: Základy uvolňování paměti
description: Zjistěte, jak funguje systém uvolňování paměti a jak jej lze nakonfigurovat pro optimální výkon.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400538"
---
# <a name="fundamentals-of-garbage-collection"></a>Základy uvolňování paměti

V clr (COMMON Language runtime) slouží systém uvolňování paměti jako automatický správce paměti. Poskytuje následující výhody:

- Umožňuje vyvíjet aplikaci bez nutnosti ručně uvolnit paměť.

- Přiděluje objekty na spravované haldy efektivně.

- Uvolní objekty, které se již nepoužívají, vymaže jejich paměť a udržuje paměť k dispozici pro budoucí přidělení. Spravované objekty automaticky získat čistý obsah začít, takže jejich konstruktory nemusí inicializovat každé datové pole.

- Poskytuje bezpečnost paměti tím, že se ujistí, že objekt nemůže použít obsah jiného objektu.

Tento článek popisuje základní koncepty uvolňování paměti.

## <a name="fundamentals-of-memory"></a>Základy paměti

Následující seznam shrnuje důležité koncepty paměti CLR.

- Každý proces má svůj vlastní, samostatný virtuální adresní prostor. Všechny procesy ve stejném počítači sdílejí stejnou fyzickou paměť a stránkovací soubor, pokud existuje.

- Ve výchozím nastavení má každý proces v 32bitových počítačích virtuální adresní prostor v uživatelském režimu 2 GB.

- Jako vývojář aplikace pracujete pouze s virtuálním adresovým prostorem a nikdy nemanipulujete s fyzickou pamětí přímo. Systém uvolňování paměti přiděluje a uvolňuje virtuální paměť pro vás na spravované haldy.

  Pokud píšete nativní kód, můžete používat funkce systému Windows pro práci s virtuálním adresovým prostorem. Tyto funkce přidělit a uvolnit virtuální paměť pro vás na nativní hromady.

- Virtuální paměť může být ve třech stavech:

  - Zdarma. Blok paměti nemá žádné odkazy na něj a je k dispozici pro přidělení.

  - Vyhrazeno. Blok paměti je k dispozici pro vaše použití a nelze jej použít pro žádný jiný požadavek na přidělení. Však nelze ukládat data do tohoto bloku paměti, dokud je potvrzena.

  - Zavázala. Blok paměti je přiřazen fyzickému úložišti.

- Virtuální adresní prostor může být fragmentován. To znamená, že v adresním prostoru jsou volné bloky, známé také jako díry. Je-li požadováno přidělení virtuální paměti, správce virtuální paměti musí najít jeden volný blok, který je dostatečně velký, aby splňoval tento požadavek na přidělení. I v případě, že máte 2 GB volného místa, přidělení, které vyžaduje 2 GB bude neúspěšné, pokud všechny, které volné místo je v jednom bloku adresy.

- Pokud není dostatek virtuálního adresového prostoru k rezervaci nebo fyzického místa k potvrzení, můžete dojít paměť.

  Stránkovací soubor se používá i v případě, že fyzický tlak paměti (tj. poptávka po fyzické paměti) je nízká. Při prvním fyzickém tlaku paměti je vysoká, operační systém musí vytvořit místo ve fyzické paměti pro ukládání dat a zálohuje některá data, která je ve fyzické paměti do stránkovacího souboru. Tato data nejsou stránkována, dokud není potřeba, takže je možné se setkat stránkování v situacích, kdy je nízký tlak fyzické paměti.

## <a name="conditions-for-a-garbage-collection"></a>Podmínky pro uvolnění paměti

Uvolnění paměti dochází, pokud je splněna jedna z následujících podmínek:

- Systém má nedostatek fyzické paměti. To je detekováno oznámením nedostatku paměti z operačního systému nebo nedostatku paměti, jak je uvedeno hostitelem.

- Paměť, která je používána přidělené objekty na spravované haldy překračuje přijatelnou prahovou hodnotu. Tato prahová hodnota je průběžně upravována při spuštění procesu.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> je volána. Téměř ve všech případech není třeba volat tuto metodu, protože uvolňování systém běží nepřetržitě. Tato metoda se používá především pro jedinečné situace a testování.

## <a name="the-managed-heap"></a>Spravovanou haldu

Po systému uvolňování paměti je inicializován clr, přiděluje segment paměti pro ukládání a správu objektů. Tato paměť se nazývá spravované haldy, na rozdíl od nativní haldy v operačním systému.

Pro každý spravovaný proces existuje spravovaná halda. Všechna vlákna v procesu přidělit paměť pro objekty na stejné haldě.

Chcete-li rezervovat paměť, systém uvolňování paměti volá funkci Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a rezervuje jeden segment paměti najednou pro spravované aplikace. Systém uvolňování paměti také podle potřeby rezervuje segmenty a uvolní segmenty zpět do operačního systému (po jejich vymazání všech objektů) voláním funkce Windows [VirtualFree.](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)

> [!IMPORTANT]
> Velikost segmentů přidělených systémem uvolňování paměti je specifická pro implementaci a může se kdykoli změnit, včetně pravidelných aktualizací. Vaše aplikace by nikdy neměla dělat předpoklady o konkrétní velikosti segmentu nebo na ní záviset, ani by se neměla pokoušet nakonfigurovat množství paměti, která je k dispozici pro přidělení segmentu.

Méně objektů přidělených na haldě, méně práce systému uvolňování paměti musí provést. Při přidělování objektů nepoužívejte hodnoty zaobleného nahoru, které přesahují vaše potřeby, například přidělení pole 32 bajtů, když potřebujete pouze 15 bajtů.

Při uvolnění paměti je spuštěna, uvolňování paměti uvolní paměť, která je obsazena mrtvé objekty. Proces rekultivace komprimuje živé objekty tak, aby byly přesunuty společně a mrtvý prostor je odebrán, čímž se halda menší. Tím je zajištěno, že objekty, které jsou přiděleny společně zůstat společně na spravované haldy, zachovat jejich lokalitu.

Rušivost (frekvence a trvání) uvolňování paměti je výsledkem objemu přidělení a množství paměti, která přežila na spravované haldě.

Haldy lze považovat za akumulaci dvou hald: [haldy velkého objektu](large-object-heap.md) a haldy malého objektu.

[Haldy velkých objektů](large-object-heap.md) obsahuje velmi velké objekty, které jsou 85 000 bajtů a větší. Objekty na haldě velkého objektu jsou obvykle matice. Je vzácné pro objekt instance být velmi velké.

> [!TIP]
> Můžete [nakonfigurovat velikost prahové hodnoty](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pro objekty jít na haldy velkého objektu.

## <a name="generations"></a>Generace

Halda je uspořádána do generací tak, aby mohla zpracovávat dlouhodobé a krátkodobé objekty. Uvolňování paměti dochází především s rekultivací krátkodobé objekty, které obvykle zabírají pouze malou část haldy. Existují tři generace objektů na haldě:

- **Generace 0**. Jedná se o nejmladší generaci a obsahuje krátkodobé objekty. Příkladem krátkodobého objektu je dočasná proměnná. Uvolňování paměti dochází nejčastěji v této generaci.

  Nově přidělené objekty tvoří novou generaci objektů a jsou implicitně generace 0 kolekce. Však pokud jsou velké objekty, přejdou na haldy velkého objektu v kolekci generace 2.

  Většina objektů jsou uvolněny pro uvolnění paměti v generaci 0 a nepřežijí další generace.

- **Generace 1**. Tato generace obsahuje krátkodobé objekty a slouží jako vyrovnávací paměť mezi krátkodobé objekty a dlouhodobé objekty.

- **Generace 2**. Tato generace obsahuje objekty s dlouhou životností. Příkladem objektu s dlouhou životností je objekt v serverové aplikaci, který obsahuje statická data, která jsou aktivní po dobu trvání procesu.

Uvolňování paměti dojít na konkrétní generace jako podmínky rozkaz. Shromažďování generace znamená shromažďování předmětů v této generaci a všech jejích mladších generacích. Uvolnění paměti generace 2 je také známé jako úplné uvolnění paměti, protože uvolňuje všechny objekty ve všech generacích (to znamená, že všechny objekty ve spravované haldě).

### <a name="survival-and-promotions"></a>Přežití a propagace

Objekty, které nejsou uvolněny v uvolňování paměti jsou označovány jako survivors a jsou povýšeny na další generaci. Objekty, které přežijí uvolnění paměti generace 0, jsou povýšeny na generaci 1; objekty, které přežijí uvolnění paměti generace 1, jsou povýšeny na generaci 2; a objekty, které přežijí uvolnění paměti generace 2 zůstávají v generaci 2.

Když systém uvolňování paměti zjistí, že míra přežití je vysoká v generaci, zvýší prahovou hodnotu přidělení pro toto generování. Další kolekce získá značnou velikost regenerované paměti. CLR neustále vyvažuje dvě priority: nenechat pracovní sadu aplikace příliš velké zpožděním uvolňování paměti a neumožňuje uvolnění paměti spustit příliš často.

### <a name="ephemeral-generations-and-segments"></a>Pomíjivé generace a segmenty

Protože objekty v generacích 0 a 1 jsou krátkodobé, tyto generace jsou známé jako dočasné generace.

Dočasné generace musí být přiděleny v segmentu paměti, který je označován jako dočasný segment. Každý nový segment získaný systémem uvolňování paměti se stane novým dočasným segmentem a obsahuje objekty, které přežily uvolnění paměti generace 0. Starý dočasný segment se stává segmentem nové generace 2.

Velikost dočasného segmentu se liší v závislosti na tom, zda je systém 32bitový nebo 64bitový a na typu systému uvolňování paměti, který je spuštěn. Výchozí hodnoty jsou uvedeny v následující tabulce.

||32bitová|64bitová|
|-|-------------|-------------|
|Pracovní stanice GC|16 MB|256 MB|
|Server GC|64 MB|4 GB|
|Server GC s logickými procesory > 4|32 MB|2 GB|
|Server GC s logickými procesory > 8|16 MB|1 GB|

Dočasný segment může obsahovat objekty generace 2. Generace 2 objekty mohou používat více segmentů (tolik, kolik vyžaduje proces a paměť umožňuje).

Množství uvolněné paměti z dočasné uvolňování paměti je omezena na velikost dočasného segmentu. Množství paměti, která je uvolněna, je úměrná prostoru, který byl obsazen mrtvými objekty.

## <a name="what-happens-during-a-garbage-collection"></a>Co se stane během uvolňování paměti

Uvolnění paměti má následující fáze:

- Fáze značení, která vyhledá a vytvoří seznam všech živých objektů.

- Fáze přemístění, která aktualizuje odkazy na objekty, které budou komprimovány.

- Fáze komprimace, která uvolňuje prostor obsazený mrtvými objekty a komprimuje přežívající objekty. Fáze komprimace přesune objekty, které přežily uvolňování paměti směrem ke staršímu konci segmentu.

  Vzhledem k tomu, že kolekce generace 2 mohou zabírat více segmentů, objekty, které jsou povýšeny na generaci 2, lze přesunout do staršího segmentu. Generace 1 i generace 2, které přežily, mohou být přesunuty do jiného segmentu, protože jsou povýšeni na generaci 2.

  Obvykle haldy velkých objektů (LOH) není komprimován, protože kopírování velkých objektů ukládá snížení výkonu. V .NET Core a v rozhraní .NET Framework 4.5.1 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> a novějších však můžete vlastnost použít k komprimaci haldy velkých objektů na vyžádání. Kromě toho je LOH automaticky zhutněn, když je nastaven pevný limit, a to zadáním:

  - limit paměti na kontejneru, nebo
  - Možnosti konfigurace [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) nebo [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Systém uvolňování paměti používá následující informace k určení, zda jsou objekty aktivní:

- **Kořeny zásobníku**. Proměnné zásobníku poskytované kompilátorem just-in-time (JIT) a tchytačivým zásobníkem. Jit optimalizace můžete prodloužit nebo zkrátit oblasti kódu, ve kterém jsou hlášeny proměnné zásobníku do systému uvolňování paměti.

- **Popisovače uvolňování paměti**. Zpracovává, které odkazují na spravované objekty a které mohou být přiděleny podle uživatelského kódu nebo běžného jazyka runtime.

- **Statická data**. Statické objekty v aplikačních doménách, které mohou odkazovat na jiné objekty. Každá doména aplikace sleduje své statické objekty.

Před spuštěním uvolňování paměti jsou všechna spravovaná vlákna pozastavena s výjimkou vlákna, které spustilo uvolňování paměti.

Následující obrázek znázorňuje vlákno, které aktivuje uvolňování paměti a způsobí, že ostatní vlákna mají být pozastavena.

![Když vlákno aktivuje uvolňování paměti](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulace s nespravovanými prostředky

Pokud spravované objekty odkazují na nespravované objekty pomocí jejich nativních popisovačů souborů, musíte explicitně uvolnit nespravované objekty, protože systém uvolňování paměti sleduje pouze paměť na spravované haldě.

Uživatelé spravovaného objektu nesmí nakládat nativní prostředky používané objektem. Chcete-li provést vyčištění, můžete provést spravovaný objekt finalizovat. Dokončení se skládá z akcí vyčištění, které se provádějí, když se objekt již nepoužívá. Když spravovaný objekt zemře, provede akce vyčištění, které jsou zadány v jeho finalizační metody.

Když je zjistit, že finalizovatelný objekt je mrtvý, jeho finalizační metoda je umístěna do fronty tak, aby byly provedeny jeho akce vyčištění, ale samotný objekt je povýšen na další generaci. Proto budete muset počkat, až další uvolnění paměti, ke kterému dochází na této generace (což není nutně další uvolnění paměti) k určení, zda byl objekt uvolněn.

Další informace o dokončení <xref:System.Object.Finalize?displayProperty=nameWithType>naleznete v tématu .

## <a name="workstation-and-server-garbage-collection"></a>Uvolňování paměti pracovní stanice a serveru

Systém uvolňování paměti je samoladný a může pracovat v široké škále scénářů. [Nastavení konfiguračního souboru](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) můžete použít k nastavení typu uvolňování paměti na základě charakteristik pracovního vytížení. CLR poskytuje následující typy uvolňování paměti:

- Uvolňování paměti pracovní stanice (GC) je určen pro klientské aplikace. Jedná se o výchozí variantu GC pro samostatné aplikace. Pro hostované aplikace, například ty, které hostuje ASP.NET, hostitel určuje výchozí gc příchuť.

  Uvolňování paměti pracovní stanice může být souběžné nebo nesouběžné. Souběžné uvolňování paměti umožňuje spravovaným vláknům pokračovat v operacích během uvolňování paměti. [Uvolňování paměti na pozadí](#background-workstation-garbage-collection) nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) v rozhraní .NET Framework 4 a novějších verzích.

- Uvolňování paměti serveru, který je určen pro serverové aplikace, které vyžadují vysokou propustnost a škálovatelnost.

  - V .NET Core může být uvolňování paměti serveru nesouběžné nebo na pozadí.

  - V rozhraní .NET Framework 4.5 a novějších verzích může být uvolňování paměti serveru nesouběžné nebo na pozadí (uvolňování paměti na pozadí nahrazuje souběžné uvolňování paměti). V rozhraní .NET Framework 4 a předchozích verzích je uvolňování paměti serveru nesouběžné.

Následující obrázek znázorňuje vyhrazená vlákna, která provádějí uvolňování paměti na serveru:

![Vlákna uvolňování paměti serveru](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Porovnat uvolňování paměti pracovní stanice a serveru

Níže jsou zřetězení a výkon aspekty pro uvolňování paměti pracovní stanice:

- Kolekce dochází ve vlákně uživatele, který spustil uvolňování paměti a zůstává na stejnou prioritu. Vzhledem k tomu, že vlákna uživatele obvykle běží s normální prioritou, systém uvolňování paměti (který běží v normálním vlákně s prioritou) musí soutěžit s jinými vlákny pro čas procesoru. (Vlákna, která spouštějí nativní kód, nejsou pozastavena na serveru ani na uvolnění paměti pracovní stanice.)

- Uvolňování paměti pracovní stanice se vždy používá v počítači, který má pouze jeden procesor, bez ohledu na [nastavení konfigurace](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Následují aspekty zřetězení a výkonu pro uvolnění paměti serveru:

- Kolekce se vyskytuje na více vyhrazených `THREAD_PRIORITY_HIGHEST` podprocesů, které jsou spuštěny na úrovni priority.

- Haldy a vyhrazené vlákno k provedení uvolňování paměti jsou k dispozici pro každý procesor a haldy jsou shromažďovány ve stejnou dobu. Každá halda obsahuje haldu malého objektu a haldu velkého objektu a všechny haldy jsou přístupné podle uživatelského kódu. Objekty na různých hromadách mohou odkazovat na sebe navzájem.

- Vzhledem k tomu, že více podprocesů uvolňování paměti spolupracovat, uvolňování paměti serveru je rychlejší než uvolňování paměti pracovní stanice na stejné haldy velikosti.

- Uvolňování paměti serveru má často větší segmenty velikosti. Toje však pouze generalizace: velikost segmentu je specifické pro implementaci a může se změnit. Neprovádělte předpoklady o velikosti segmentů přidělených systémem uvolňování paměti při ladění aplikace.

- Uvolňování paměti serveru může být náročné na prostředky. Představte si například, že existuje 12 procesů, které používají server GC spuštěné v počítači, který má 4 procesory. Pokud všechny procesy náhodou sbírat odpadky ve stejnou dobu, by zasahovali do sebe, protože by bylo 12 podprocesů naplánovaných na stejném procesoru. Pokud jsou procesy aktivní, není vhodné, aby všechny používaly server GC.

Pokud používáte stovky instancí aplikace, zvažte použití uvolňování paměti pracovní stanice s uvolňování souběžných uvolňování paměti zakázáno. To bude mít za následek méně přepínání kontextu, což může zlepšit výkon.

## <a name="background-workstation-garbage-collection"></a>Uvolňování paměti pracovní stanice na pozadí

V uvolňování paměti pracovní stanice na pozadí dočasné generace (0 a 1) jsou shromažďovány podle potřeby, zatímco kolekce generace 2 probíhá. Uvolňování paměti pracovní stanice na pozadí se provádí ve vyhrazeném vlákně a platí pouze pro kolekce generace 2.

Uvolňování paměti na pozadí je ve výchozím nastavení povoleno a může být povoleno nebo zakázáno nastavením [konfigurace gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) v aplikacích rozhraní .NET Framework nebo v aplikacích [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) v aplikacích .NET Core.

> [!NOTE]
> Uvolňování paměti na pozadí nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) a je k dispozici v rozhraní .NET Framework 4 a novějších verzích. V rozhraní .NET Framework 4 je podporována pouze pro uvolňování paměti pracovní stanice. Počínaje rozhraním .NET Framework 4.5 je k dispozici uvolňování paměti na pozadí pro uvolňování paměti pracovní stanice i serveru.

Kolekce na dočasné generace během uvolňování paměti na pozadí se označuje jako uvolňování paměti popředí. Dojde-li k uvolnění paměti v popředí, jsou pozastavena všechna spravovaná vlákna.

Pokud probíhá uvolňování paměti na pozadí a v generaci 0 jste přidělili dostatek objektů, clr provádí generování 0 nebo generace 1 uvolňování paměti na popředí. Vyhrazené vlákno uvolňování paměti na pozadí kontroluje v častých bezpečných bodech k určení, zda existuje požadavek na uvolnění paměti v popředí. Pokud existuje, kolekce pozadí pozastaví sám tak, aby může dojít k uvolňování paměti popředí. Po dokončení uvolňování paměti na popředí, vyhrazené vlákno uvolňování paměti na pozadí a vlákna uživatele pokračovat.

Uvolňování paměti na pozadí odebere omezení přidělení uložená souběžným uvolňováním paměti, protože dočasné uvolnění paměti může nastat během uvolňování paměti na pozadí. Uvolňování paměti na pozadí může odebrat nevrácené objekty v dočasných generacích. Může také rozbalit haldy v případě potřeby během uvolnění paměti generace 1.

Následující obrázek znázorňuje uvolňování paměti na pozadí prováděné v samostatném vyhrazeném vlákně na pracovní stanici:

![Uvolňování paměti pracovní stanice na pozadí](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Uvolnění paměti serveru na pozadí

Počínaje rozhraním .NET Framework 4.5 je uvolnění paměti serveru na pozadí výchozím režimem pro uvolnění paměti serveru.

Funkce uvolňování paměti serveru na pozadí podobně jako uvolňování paměti pracovní stanice na pozadí, popsané v předchozí části, ale existuje několik rozdílů:

- Uvolňování paměti pracovní stanice na pozadí používá jedno vyhrazené vlákno uvolňování paměti na pozadí, zatímco uvolňování paměti serveru na pozadí používá více vláken. Obvykle je vyhrazené vlákno pro každý logický procesor.

- Na rozdíl od vlákna uvolňování paměti na pozadí pracovní stanice tyto podprocesy nečasový mat.

Následující obrázek znázorňuje uvolňování paměti na pozadí prováděné v samostatném vyhrazeném vlákně na serveru:

![Uvolnění paměti serveru na pozadí](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti

> [!TIP]
> Tento oddíl se vztahuje na:
>
> - Rozhraní .NET Framework 3.5 a starší pro uvolňování paměti pracovní stanice
> - Rozhraní .NET Framework 4 a starší pro uvolnění paměti serveru
>
> Souběžné nesmysly jsou nahrazeny [uvolňováním paměti na pozadí](#background-workstation-garbage-collection) v novějších verzích.

V uvolňování paměti pracovní stanice nebo serveru můžete [povolit souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), které umožňuje souběžné spuštění vláken s vyhrazeným vláknem, které provádí uvolňování paměti po většinu doby trvání kolekce. Tato možnost ovlivňuje pouze uvolňování paměti v generaci 2; generace 0 a 1 jsou vždy nesouběžné, protože končí velmi rychle.

Souběžné uvolňování paměti umožňuje interaktivní masy lépe reagovat minimalizací pauzy pro kolekci. Spravovaná vlákna mohou pokračovat ve většině času při spuštění souběžného vlákna uvolňování paměti. To má za následek kratší pauzy při uvolňování paměti dochází.

Souběžné uvolňování paměti se provádí ve vyhrazeném vlákně. Ve výchozím nastavení clr spustí uvolňování paměti pracovní stanice s povolenou souběžnou uvolňování paměti. To platí pro počítače s jedním procesorem a více procesory.

Následující obrázek znázorňuje souběžné uvolňování paměti prováděné v samostatném vyhrazeném vlákně.

![Souběžná vlákna uvolňování paměti](./media/gc-concurrent.png)

## <a name="see-also"></a>Viz také

- [Možnosti konfigurace pro gc](../../core/run-time-config/garbage-collector.md)
- [Uvolněné](index.md)
