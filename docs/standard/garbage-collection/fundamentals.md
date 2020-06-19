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
ms.openlocfilehash: 438188b6d694bdeab772c43ef92e5621c68facff
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990216"
---
# <a name="fundamentals-of-garbage-collection"></a>Základní informace o uvolňování paměti

V modulu CLR (Common Language Runtime) slouží systém uvolňování paměti (GC) jako automatický správce paměti. Systém uvolňování paměti spravuje přidělování a uvolňování paměti aplikace. Pro vývojáře, kteří pracují se spravovaným kódem, to znamená, že nemusíte psát kód pro provádění úloh správy paměti. Automatická správa paměti může eliminovat běžné problémy, například forgetting k uvolnění objektu a příčinou nevrácení paměti nebo pokusu o přístup k paměti pro objekt, který je již uvolněn.

Tento článek popisuje základní koncepty uvolňování paměti.

## <a name="benefits"></a>Výhody

Systém uvolňování paměti přináší následující výhody:

- Uvolňuje vývojářům, aby nemuseli ručně uvolnit paměť.

- Přiděluje objekty na spravované haldě efektivně.

- Redeklarace objektů, které se již nepoužívají, vymaže jejich paměť a udržuje dostupnou paměť pro budoucí přidělení. Spravované objekty automaticky dostanou čistým obsahem, takže jejich konstruktory nemusí inicializovat každé datové pole.

- Zajišťuje bezpečnost paměti tím, že zajistí, že objekt nemůže použít obsah jiného objektu.

## <a name="fundamentals-of-memory"></a>Základy paměti

Následující seznam shrnuje důležité koncepty paměti CLR.

- Každý proces má vlastní, oddělený virtuální adresní prostor. Všechny procesy ve stejném počítači sdílejí stejnou fyzickou paměť a stránkovací soubor, pokud je nějaký.

- Ve výchozím nastavení na 32 počítačích má každý proces virtuální adresní prostor 2 GB v uživatelském režimu.

- Jako vývojář aplikací pracujete jenom s virtuálním adresním prostorem a nikdy nepracujete s fyzickou pamětí přímo. Systém uvolňování paměti přiděluje a uvolňuje virtuální paměť na spravované haldě.

  Pokud píšete nativní kód, použijte funkce systému Windows pro práci s virtuálním adresním prostorem. Tyto funkce přidělují a uvolňují virtuální paměti pro vás na nativních haldách.

- Virtuální paměť může být ve třech stavech:

  | State | Popis |
  |---------|---------|
  | Free | Blok paměti neobsahuje žádné odkazy a je k dispozici pro přidělení. |
  | Vyhrazeno | Blok paměti je k dispozici pro vaše použití a nelze jej použít pro žádnou jinou žádost o přidělení. Do tohoto bloku paměti však nelze ukládat data, dokud není potvrzeno. |
  | Committed | Blok paměti je přiřazený k fyzickému úložišti. |

- Virtuální adresní prostor se může fragmentovat. To znamená, že v adresním prostoru jsou k dispozici bezplatné bloky, označované také jako díry. Po vyžádání přidělení virtuální paměti musí správce virtuální paměti najít jeden bezplatný blok, který je dostatečně velký pro splnění této žádosti o přidělení. I v případě, že máte 2 GB volného místa, přidělení, které vyžaduje 2 GB, bude neúspěšné, pokud všechny volné místo nejsou v jednom bloku adres.

- Pokud není k dispozici dostatek adresního prostoru pro rezervaci nebo fyzické místo pro potvrzení, můžete nedostatek paměti.

  Stránkovací soubor se používá i v případě, že je nízká tlak fyzické paměti (tj. poptávka pro fyzickou paměť). Při prvním vysokém zatížení fyzické paměti musí operační systém uvolnit místo ve fyzické paměti pro ukládání dat a pak zálohuje některá data, která jsou ve fyzické paměti pro stránkovací soubor. Tato data nejsou stránkovaná, dokud je nepotřebujete, takže je možné vyskytnout stránkování v situacích, kdy je nízký tlak fyzické paměti.
  
### <a name="memory-allocation"></a>Přidělení paměti

Při inicializaci nového procesu vyhradí modul runtime souvislou oblast adresního prostoru pro daný proces. Tento vyhrazený adresní prostor se nazývá spravovaná halda. Spravovaná halda udržuje ukazatel na adresu, kde bude přidělen další objekt v haldě. Zpočátku je tento ukazatel nastavený na základní adresu spravované haldy. Všechny typy odkazů jsou přiděleny na spravovanou haldu. Když aplikace vytvoří první typ odkazu, přidělí se paměť pro typ na základní adrese spravované haldy. Když aplikace vytvoří další objekt, systém uvolňování paměti přidělí paměť v adresním prostoru hned za prvním objektem. Pokud je k dispozici adresní prostor, uvolňování paměti pro nové objekty tímto způsobem stále přiděluje místo.

Přidělování paměti ze spravované haldy je rychlejší než nespravované přidělení paměti. Vzhledem k tomu, že modul Runtime přiděluje paměť pro objekt přidáním hodnoty na ukazatel, je téměř stejně rychlá jako přidělování paměti ze zásobníku. Kromě toho vzhledem k tomu, že nové objekty, které jsou přiděleny po sobě, jsou uloženy souvisle ve spravované haldě, aplikace může přistupovat k objektům rychle.

### <a name="memory-release"></a>Verze paměti

Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení kolekce na základě přidělení. Když systém uvolňování paměti provede kolekci, uvolní paměť pro objekty, které již aplikace nepoužívá. Určuje, které objekty již nejsou používány, prozkoumáním *kořenů*aplikace. Kořeny aplikace zahrnují statická pole, místní proměnné a parametry v zásobníku vlákna a Registry procesoru. Každý kořenový adresář buď odkazuje na objekt na spravované haldě, nebo je nastaven na hodnotu null. Systém uvolňování paměti má přístup k seznamu aktivních kořenových adresářů, které kompilátor JIT (just-in-time) a modul runtime udržují. Pomocí tohoto seznamu vytvoří systém uvolňování paměti graf, který obsahuje všechny objekty, které jsou dosažitelné z kořenů.

Objekty, které nejsou v grafu, jsou nedosažitelné z kořenů aplikace. Systém uvolňování paměti považuje nedosažitelné objekty za paměti a uvolní přidělenou paměť. V průběhu kolekce systém uvolňování paměti ověřuje spravovanou haldu a hledá bloky adresního prostoru obsazené nedosažitelnými objekty. Vzhledem k tomu, že zjistí každý nedosažitelný objekt, používá funkci kopírování paměti pro komprimaci dosažitelných objektů v paměti a uvolní bloky adresních prostorů přidělených nedostupným objektům. Po komprimaci paměti pro dostupné objekty provede systém uvolňování paměti nezbytné opravy ukazatelů, aby kořeny aplikace odkazovaly na objekty v jejich nových umístěních. Také umístí ukazatel spravované haldy za poslední dosažitelný objekt.

Paměť je komprimována pouze v případě, že kolekce zjistí významný počet nedosažitelných objektů. Pokud všechny objekty ve spravované haldě přestanou kolekci, nepotřebujete komprimaci paměti.

Za účelem zvýšení výkonu přiděluje modul runtime paměť pro velké objekty v samostatné haldě. Systém uvolňování paměti automaticky uvolňuje paměť pro velké objekty. Chcete-li se ale vyhnout přesunutí velkých objektů v paměti, obvykle se tato paměť nekomprimuje.

## <a name="conditions-for-a-garbage-collection"></a>Podmínky pro uvolňování paměti

Uvolňování paměti nastane, pokud je splněna jedna z následujících podmínek:

- Systém má nedostatek fyzické paměti. Tato možnost je zjištěna buď pomocí oznámení o nedostatku paměti z operačního systému, nebo z nedostatku paměti, jak je uvedeno v hostiteli.

- Paměť, kterou používá přidělené objekty na spravované haldě, překročí přijatelnou prahovou hodnotu. Tato prahová hodnota je průběžně upravována při spuštění procesu.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType>Metoda je volána. Ve většině případů nemusíte volat tuto metodu, protože systém uvolňování paměti běží nepřetržitě. Tato metoda se primárně používá pro jedinečné situace a testování.

## <a name="the-managed-heap"></a>Spravovaná halda

Po inicializaci uvolňování paměti modulem CLR přidělí segment paměti pro ukládání a správu objektů. Tato paměť se nazývá spravovaná halda, nikoli nativní halda v operačním systému.

Pro každý spravovaný proces existuje spravovaná halda. Všechna vlákna v procesu přidělují paměť pro objekty ve stejné haldě.

Pro vyhradení paměti systém uvolňování paměti zavolá funkci Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) a rezervuje pro spravované aplikace jeden segment paměti. Systém uvolňování paměti také vyhrazuje segmenty, jak je potřeba, a uvolní segmenty zpátky do operačního systému (po vymazání všech objektů) voláním funkce [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) systému Windows.

> [!IMPORTANT]
> Velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelných aktualizací. Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.

Čím méně objektů bylo přiděleno haldě, tím méně práce musí systém uvolňování paměti dělat. Při přidělování objektů nepoužívejte zaoblené hodnoty, které překračují vaše potřeby, jako je například přidělení pole 32 bajtů, pokud potřebujete pouze 15 bajtů.

Když je aktivováno uvolňování paměti, uvolňování paměti uvolní paměť, která je obsazena mrtvými objekty. Proces opětovného získání komprimuje živé objekty tak, aby se přesunuly dohromady, a nedoručené místo se odebere, takže halda bude menší. Tím se zajistí, aby objekty, které jsou přiděleny dohromady, zůstaly na spravované haldě, aby se zachovala jejich místní aktuálnost.

Rušivost (četnost a doba trvání) uvolňování paměti je výsledkem objemu přidělení a množství zachované paměti na spravované haldě.

Halda může být považována za akumulaci dvou hald: [halda velkých objektů](large-object-heap.md) a haldy malých objektů. Halda velkých objektů obsahuje objekty, které jsou 85 000 bajtů a větší, což jsou obvykle pole. Pro objekt instance je zřídka velká.

> [!TIP]
> Můžete [nakonfigurovat prahovou velikost](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pro objekty, které mají být v haldě velkých objektů.

## <a name="generations"></a>Všechna

Algoritmus GC je založený na několika ohledech:

- Je rychlejší komprimovat paměť pro část spravované haldy, než pro celou spravovanou haldu.
- Novější objekty mají kratší životnost a starší objekty mají delší životnost.
- Novější objekty by měly být vzájemně vzájemně propojené a k nim přistupují aplikace po stejnou dobu.

K uvolňování paměti dochází hlavně v případě opětovného získávání krátkodobých objektů. Pro optimalizaci výkonu uvolňování paměti je spravovaná halda rozdělena na tři generace, 0, 1 a 2, takže může zpracovávat dlouhodobé a krátkodobé objekty samostatně. Systém uvolňování paměti ukládá nové objekty v generaci 0. Objekty vytvořené na začátku v životním cyklu aplikace, které jsou převedené na kolekce, jsou povýšeny a uloženy v generacích 1 a 2. Vzhledem k tomu, že je rychlejší komprimovat část spravované haldy, než je celá halda, toto schéma umožňuje uvolňování paměti uvolnit paměť v konkrétní generaci místo uvolnění paměti pro celou spravovanou haldu pokaždé, když aplikace provede kolekci.

- **Generace 0**. Toto je nejmladšího sourozence generace a obsahuje krátkodobé objekty. Příkladem krátkodobého objektu je dočasná proměnná. K uvolňování paměti dochází nejčastěji v této generaci.

  Nově přidělené objekty tvoří novou generaci objektů a jsou implicitními kolekcemi 0. generace. Pokud se však jedná o velké objekty, přejdou na haldu velkých objektů (LOH), což je někdy označováno jako *generace 3*. Generace 3 je fyzická generace, která je logicky shromažďována jako součást generace 2.

  Většina objektů se uvolní pro uvolňování paměti v generaci 0 a nepřekoná se k další generaci.
  
  Pokud se aplikace pokusí vytvořit nový objekt, když je generace 0 plná, systém uvolňování paměti provede kolekci v pokusu o uvolnění adresního prostoru pro daný objekt. Systém uvolňování paměti začíná prozkoumáním objektů v generaci 0 místo všech objektů ve spravované haldě. Kolekce samotné generace 0 často uvolňuje dostatek paměti, aby mohla aplikace pokračovat v vytváření nových objektů.

- **Generace 1**. Tato generace obsahuje krátkodobé objekty a slouží jako vyrovnávací paměť mezi krátkodobé a dlouhodobé objekty.

  Jakmile systém uvolňování paměti provede kolekci generace 0, zkomprimuje paměť pro dostupné objekty a propaguje je na generaci 1. Vzhledem k tomu, že objekty, které zachují kolekce, mají obvykle delší životnost, je vhodné je zvýšit na vyšší generaci. Systém uvolňování paměti nemusí přezkoumávat objekty v generacích 1 a 2 pokaždé, když provede kolekci generace 0.
  
  Pokud kolekce generace 0 neuvolní dostatek paměti pro aplikaci, aby vytvořila nový objekt, může systém uvolňování paměti provést kolekci 1. generace a pak 2. generace. Objekty v generaci 1, které dodržely kolekce, jsou povýšeny na generaci 2.

- **Generace 2**. Tato generace obsahuje dlouhodobě nedlouhodobé objekty. Příkladem dlouhotrvajícího objektu je objekt v serverové aplikaci, který obsahuje statická data, která jsou po dobu trvání procesu aktivní.

  Objekty v generaci 2, které dodržely kolekci, zůstávají v generaci 2, dokud nebudou v budoucí kolekci nedostupné.
  
  Objekty v haldě velkých objektů (což je někdy označováno jako *generace 3*) jsou shromažďovány také v generaci 2.

K uvolňování paměti dochází na určitých generacích, protože podmínky zaručují. Shromáždění generace znamená shromažďování objektů v této generaci a všech jejích mladších generací. Uvolňování paměti 2. generace se označuje také jako úplné uvolňování paměti, protože objekty ve všech generacích (tj. všechny objekty ve spravované haldě) uvolňují.

### <a name="survival-and-promotions"></a>Přežití a propagační akce

Objekty, které nejsou znovu získány v uvolňování paměti, jsou označovány jako zachované a jsou povýšeny na novou generaci:

- Objekty, které jsou zachovány uvolňováním paměti generace 0, jsou povýšeny na generaci 1.
- Objekty, které jsou zachovány uvolňováním paměti generace 1, jsou povýšeny na generaci 2.
- Objekty, které jsou v procesu uvolňování paměti generace 2, zůstávají v generaci 2.

Když systém uvolňování paměti zjistí, že je míra přežití v generaci vysoká, zvyšuje se prahová hodnota přidělení pro tuto generaci. Další kolekce získá značnou velikost uvolněné paměti. CLR průběžně vyrovnává dvě priority: Pokud nechcete, aby pracovní sada aplikace byla příliš velká, pomocí opožděného uvolňování paměti a neumožnilo spouštění uvolňování paměti příliš často.

### <a name="ephemeral-generations-and-segments"></a>Dočasné generace a segmenty

Vzhledem k tomu, že objekty v generacích 0 a 1 jsou krátkodobé, tyto generace jsou známy jako *dočasné generace*.

Dočasné generace jsou přiděleny v segmentu paměti, který je známý jako dočasný segment. Každý nový segment získaný systémem uvolňování paměti se stal novým dočasným segmentem a obsahuje objekty, které předržely uvolňování paměti generace 0. Starý dočasný segment se vytvoří jako nový segment 2. generace.

Velikost dočasného segmentu se liší v závislosti na tom, zda je systém 32 nebo 64 a na typu uvolňování paměti, které je spuštěn ([pracovní stanice nebo Server uvolňování](workstation-server-gc.md)paměti). V následující tabulce jsou uvedeny výchozí velikosti dočasného segmentu.

|Uvolňování paměti pracovní stanice/serveru|32bitová|64bitová|
|-|-------------|-------------|
|GC pracovní stanice|16 MB|256 MB|
|Uvolňování paměti serveru|64 MB|4 GB|
|GC serveru s logickými procesory > 4|32 MB|2 GB|
|Uvolňování paměti serveru s využitím > 8 logických procesorů|16 MB|1 GB|

Dočasný segment může zahrnovat objekty generace 2. Objekty generace 2 můžou používat víc segmentů (tolik, kolik je váš proces vyžaduje, a paměť umožňuje).

Velikost volné paměti z dočasného uvolňování paměti je omezená na velikost dočasného segmentu. Velikost paměti, která je uvolněna, je úměrná místu, které byly obsazeny neaktivními objekty.

## <a name="what-happens-during-a-garbage-collection"></a>Co se stane během uvolňování paměti

Uvolňování paměti má následující fáze:

- Fáze označení, která najde a vytvoří seznam všech živých objektů.

- Fáze přemístění, která aktualizuje odkazy na objekty, které budou zkomprimovány.

- Kompaktní fáze, která uvolňuje místo obsazené neaktivními objekty a komprimuje zbývající objekty. Fáze komprimace přesune objekty, které předržely uvolňování paměti směrem na starší konec segmentu.

  Vzhledem k tomu, že kolekce 2. generace mohou zabírat více segmentů, objekty, které jsou povýšeny do generace 2, lze přesunout do staršího segmentu. Generace 1 i 2, zachované, je možné přesunout do jiného segmentu, protože jsou povýšeny na generaci 2.

  Obvykle se nekomprimuje halda pro velké objekty (LOH), protože kopírování velkých objektů ukládá snížení výkonu. V rozhraní .NET Core a v .NET Framework 4.5.1 a novějších verzích ale můžete použít <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost k komprimaci haldy velkých objektů na vyžádání. Kromě toho se LOH automaticky zkomprimuje, když se nastaví pevný limit zadáním těchto znaků:

  - Omezení paměti pro kontejner.
  - [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) nebo [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) možnosti konfigurace modulu runtime.

Systém uvolňování paměti používá následující informace k určení, zda jsou objekty živé:

- **Kořeny zásobníku**. Proměnné zásobníku poskytované kompilátorem JIT (just-in-time) a zásobníkem Stack prohlížeč. Optimalizace JIT mohou prodloužit nebo zkrátit oblasti kódu, ve kterých jsou proměnné zásobníku hlášeny do uvolňování paměti.

- **Popisovače uvolňování paměti**. Obslužné rutiny, které odkazují na spravované objekty a které mohou být přiděleny uživatelským kódem nebo modulem CLR (Common Language Runtime).

- **Statická data**. Statické objekty v aplikačních doménách, které by mohly odkazovat na jiné objekty. Každá doména aplikace udržuje přehled o svých statických objektech.

Před spuštěním uvolňování paměti jsou všechna spravovaná vlákna pozastavena s výjimkou vlákna, které vyvolalo uvolňování paměti.

Následující ilustrace znázorňuje vlákno, které spouští uvolňování paměti a způsobuje pozastavení ostatních vláken.

![Když vlákno spustí uvolňování paměti](media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Nespravované prostředky

Pro většinu objektů, které vaše aplikace vytvoří, můžete spoléhat na uvolňování paměti, aby se automaticky prováděly nezbytné úlohy správy paměti. Nespravované prostředky však vyžadují explicitní vyčištění. Nejběžnějším typem nespravovaného prostředku je objekt, který balí prostředek operačního systému, jako je například popisovač souboru, popisovač okna nebo síťové připojení. I když je systém uvolňování paměti schopný sledovat životnost spravovaného objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak prostředek vyčistit.

Při vytváření objektu, který zapouzdřuje nespravovaný prostředek, je doporučeno zadat potřebný kód pro vyčištění nespravovaného prostředku ve veřejné `Dispose` metodě. Poskytnutím `Dispose` metody umožníte uživatelům vašeho objektu explicitně uvolnit svou paměť, až se dokončí s objektem. Při použití objektu, který zapouzdřuje nespravovaný prostředek, se ujistěte, že zavoláte `Dispose` podle potřeby.

Musíte také zadat způsob, jakým se mají nespravované prostředky uvolnit pro případ, že příjemce vašeho typu zapomene volání `Dispose` . Můžete buď použít bezpečný popisovač k zabalení nespravovaného prostředku, nebo přepsat <xref:System.Object.Finalize?displayProperty=nameWithType> metodu.

Další informace o čištění nespravovaných prostředků najdete v tématu [vyčištění nespravovaných prostředků](unmanaged.md).

## <a name="see-also"></a>Viz také

- [Uvolnění paměti pracovní stanice a serveru](workstation-server-gc.md)
- [Uvolňování paměti na pozadí](background-gc.md)
- [Možnosti konfigurace pro GC](../../core/run-time-config/garbage-collector.md)
- [Uvolnění paměti](index.md)
