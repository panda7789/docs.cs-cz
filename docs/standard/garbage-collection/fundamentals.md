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
ms.openlocfilehash: 1fdf7fcd61fb4bf9e8e0cbfe28842208f6eadd00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102434"
---
# <a name="fundamentals-of-garbage-collection"></a>Základy uvolňování paměti

V clr (COMMON Language runtime) slouží systém uvolňování paměti jako automatický správce paměti. Systém uvolňování paměti spravuje přidělení a uvolnění paměti pro aplikaci. Pro vývojáře pracující se spravovaným kódem to znamená, že nemusíte psát kód k provádění úloh správy paměti. Automatická správa paměti může eliminovat běžné problémy, jako je například zapomínání na uvolnění objektu a příčinou nevracení paměti nebo pokusu o přístup k paměti pro objekt, který již byl uvolněn.

Tento článek popisuje základní koncepty uvolňování paměti.

## <a name="benefits"></a>Výhody

Systém uvolňování paměti poskytuje následující výhody:

- Osvobozuje vývojáře od nutnosti ručně uvolnit paměť.

- Přiděluje objekty na spravované haldy efektivně.

- Uvolní objekty, které se již nepoužívají, vymaže jejich paměť a udržuje paměť k dispozici pro budoucí přidělení. Spravované objekty automaticky získat čistý obsah začít, takže jejich konstruktory nemusí inicializovat každé datové pole.

- Poskytuje bezpečnost paměti tím, že se ujistí, že objekt nemůže použít obsah jiného objektu.

## <a name="fundamentals-of-memory"></a>Základy paměti

Následující seznam shrnuje důležité koncepty paměti CLR.

- Každý proces má svůj vlastní, samostatný virtuální adresní prostor. Všechny procesy ve stejném počítači sdílejí stejnou fyzickou paměť a stránkovací soubor, pokud existuje.

- Ve výchozím nastavení má každý proces v 32bitových počítačích virtuální adresní prostor v uživatelském režimu 2 GB.

- Jako vývojář aplikace pracujete pouze s virtuálním adresovým prostorem a nikdy nemanipulujete s fyzickou pamětí přímo. Systém uvolňování paměti přiděluje a uvolňuje virtuální paměť pro vás na spravované haldy.

  Pokud píšete nativní kód, můžete používat funkce systému Windows pro práci s virtuálním adresovým prostorem. Tyto funkce přidělit a uvolnit virtuální paměť pro vás na nativní hromady.

- Virtuální paměť může být ve třech stavech:

  | Stav | Popis |
  |---------|---------|
  | Free | Blok paměti nemá žádné odkazy na něj a je k dispozici pro přidělení. |
  | Vyhrazeno | Blok paměti je k dispozici pro vaše použití a nelze jej použít pro žádný jiný požadavek na přidělení. Však nelze ukládat data do tohoto bloku paměti, dokud je potvrzena. |
  | Committed | Blok paměti je přiřazen fyzickému úložišti. |

- Virtuální adresní prostor může být fragmentován. To znamená, že v adresním prostoru jsou volné bloky, známé také jako díry. Je-li požadováno přidělení virtuální paměti, správce virtuální paměti musí najít jeden volný blok, který je dostatečně velký, aby splňoval tento požadavek na přidělení. I v případě, že máte 2 GB volného místa, přidělení, které vyžaduje 2 GB bude neúspěšné, pokud všechny, které volné místo je v jednom bloku adresy.

- Pokud není dostatek virtuálního adresového prostoru k rezervaci nebo fyzického místa k potvrzení, můžete dojít paměť.

  Stránkovací soubor se používá i v případě, že fyzický tlak paměti (tj. poptávka po fyzické paměti) je nízká. Při prvním fyzickém tlaku paměti je vysoká, operační systém musí vytvořit místo ve fyzické paměti pro ukládání dat a zálohuje některá data, která je ve fyzické paměti do stránkovacího souboru. Tato data nejsou stránkována, dokud není potřeba, takže je možné se setkat stránkování v situacích, kdy je nízký tlak fyzické paměti.
  
### <a name="memory-allocation"></a>Přidělení paměti

Při inicializaci nového procesu si zaběhu rezervuje souvislou oblast adresního prostoru pro proces. Tento vyhrazený adresní prostor se nazývá spravovaná halda. Spravovaná halda udržuje ukazatel na adresu, kde bude přidělen další objekt v haldě. Zpočátku tento ukazatel je nastavena na základní adresu spravované haldy. Všechny typy odkazů jsou přiděleny na spravované haldy. Když aplikace vytvoří první typ odkazu, je přidělena paměť pro typ na základní adrese spravované haldy. Když aplikace vytvoří další objekt, systém uvolňování paměti pro něj přiděluje paměť v adresním prostoru bezprostředně za prvním objektem. Tak dlouho, dokud adresní prostor je k dispozici, systém uvolňování paměti nadále přidělovat prostor pro nové objekty tímto způsobem.

Přidělení paměti ze spravované haldy je rychlejší než přidělení nespravované paměti. Vzhledem k tomu, že runtime přiděluje paměť pro objekt přidáním hodnoty k ukazateli, je téměř stejně rychlý jako přidělení paměti ze zásobníku. Navíc vzhledem k tomu, že nové objekty, které jsou přiděleny postupně, jsou uloženy souvislí ve spravované haldě, aplikace může rychle přistupovat k objektům.

### <a name="memory-release"></a>Uvolnění paměti

Optimalizační modul systému uvolňování paměti určuje nejlepší čas k provedení kolekce na základě provedených přidělení. Když systém uvolňování paměti provádí kolekci, uvolní paměť pro objekty, které již nejsou používány aplikací. Určuje, které objekty se již nepoužívají, a to zkoumáním *kořenů*aplikace . Kořeny aplikace zahrnují statická pole, místní proměnné a parametry v zásobníku vlákna a registry procesoru. Každý kořen odkazuje na objekt na spravované haldě nebo je nastavenna na hodnotu null. Systém uvolňování paměti má přístup k seznamu aktivních kořenů, které kompilátor just-in-time (JIT) a za běhu udržují. Pomocí tohoto seznamu systém uvolňování paměti vytvoří graf, který obsahuje všechny objekty, které jsou dosažitelné z kořenů.

Objekty, které nejsou v grafu jsou nedostupné z kořenů aplikace. Systém uvolňování paměti považuje nedosažitelné objekty za nesmyslné a uvolní paměť, která je pro ně přidělena. Během kolekce systém uvolňování paměti zkoumá spravované haldy, hledá bloky adresního prostoru obsazené nedosažitelné objekty. Při zjišťování každého nedosažitelného objektu používá funkci kopírování paměti k komprimaci dosažitelných objektů v paměti a uvolňuje bloky adresních prostorů přidělených nedostupným objektům. Jakmile paměť pro dosažitelné objekty byla zkomprimována, systém uvolňování paměti provede potřebné opravy ukazatele tak, aby kořeny aplikace odkazují na objekty v jejich nových umístěních. Také umístí ukazatele spravované haldy za poslední dosažitelný objekt.

Paměť je komprimována pouze v případě, že kolekce zjistí významný počet nedostupných objektů. Pokud všechny objekty ve spravované haldy přežít kolekce, pak není nutné pro zhutňování paměti.

Chcete-li zlepšit výkon, runtime přiděluje paměť pro velké objekty v samostatné haldy. Systém uvolňování paměti automaticky uvolní paměť pro velké objekty. Chcete-li se však vyhnout přesouvání velkých objektů v paměti, tato paměť obvykle není komprimována.

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

Při uvolnění paměti je spuštěna, uvolňování paměti uvolní paměť, která je obsazena mrtvé objekty. Proces rekultivace komprimuje živé objekty tak, aby byly přesunuty společně a mrtvý prostor je odebrán, čímž se halda menší. Tím je zajištěno, že objekty, které jsou přiděleny společně zůstat společně na spravované haldy zachovat jejich lokalitu.

Rušivost (frekvence a trvání) uvolňování paměti je výsledkem objemu přidělení a množství paměti, která přežila na spravované haldě.

Haldy lze považovat za akumulaci dvou hald: [haldy velkého objektu](large-object-heap.md) a haldy malého objektu. Halda velkých objektů obsahuje objekty, které jsou 85 000 bajtů a větší, což jsou obvykle pole. Je vzácné, aby byl objekt instance extrémně velký.

> [!TIP]
> Můžete [nakonfigurovat velikost prahové hodnoty](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pro objekty jít na haldy velkého objektu.

## <a name="generations"></a>Generace

Algoritmus GC je založen na několika aspektech:

- Je rychlejší komprimovat paměť pro část spravované haldy než pro celou spravovanou haldu.
- Novější objekty mají kratší životnost a starší objekty mají delší životnost.
- Novější objekty mají tendenci být vzájemně propojeny a přistupovat k nim přibližně ve stejnou dobu.

Uvolňování paměti dochází především s rekultivací krátkodobé objekty. Chcete-li optimalizovat výkon systému uvolňování paměti, spravované haldy je rozdělena do tří generací, 0, 1 a 2, takže může zpracovávat dlouhodobé a krátkodobé objekty samostatně. Systém uvolňování paměti ukládá nové objekty v generaci 0. Objekty vytvořené v rané fázi životnosti aplikace, které přežijí kolekce jsou povýšeny a uloženy v generacích 1 a 2. Vzhledem k tomu, že je rychlejší komprimovat část spravované haldy než celou haldu, toto schéma umožňuje uvolňování paměti v určité generaci, nikoli uvolnění paměti pro celou spravovanou haldu pokaždé, když provádí kolekci.

- **Generace 0**. Jedná se o nejmladší generaci a obsahuje krátkodobé objekty. Příkladem krátkodobého objektu je dočasná proměnná. Uvolňování paměti dochází nejčastěji v této generaci.

  Nově přidělené objekty tvoří novou generaci objektů a jsou implicitně generace 0 kolekce. Však pokud jsou velké objekty, přejdou na haldy velkého objektu v kolekci generace 2.

  Většina objektů jsou uvolněny pro uvolnění paměti v generaci 0 a nepřežijí na další generaci.
  
  Pokud se aplikace pokusí vytvořit nový objekt při generování 0 je plná, systém uvolňování paměti provede kolekci ve snaze uvolnit adresní prostor pro objekt. Uvolňování začíná zkoumáním objektů v generaci 0, nikoli všechny objekty ve spravované haldě. Kolekce generace 0 sám často uvolní dostatek paměti, aby aplikace pokračovat ve vytváření nových objektů.

- **Generace 1**. Tato generace obsahuje krátkodobé objekty a slouží jako vyrovnávací paměť mezi krátkodobé objekty a dlouhodobé objekty.

  Po uvolňování provede kolekci generace 0, zkomprimuje paměť pro dosažitelné objekty a povýší je na generaci 1. Protože objekty, které přežívají kolekce mají tendenci mít delší životnost, má smysl je povýšit na vyšší generaci. Systém uvolňování paměti nemusí znovu prozkoumat objekty v generacích 1 a 2 pokaždé, když provede kolekci generace 0.
  
  Pokud kolekce generace 0 neuvolněna dostatek paměti pro aplikaci k vytvoření nového objektu, systém uvolňování paměti může provést kolekci generace 1, pak generace 2. Objekty v generaci 1, které přežijí kolekce jsou povýšeny na generaci 2.

- **Generace 2**. Tato generace obsahuje objekty s dlouhou životností. Příkladem objektu s dlouhou životností je objekt v serverové aplikaci, který obsahuje statická data, která jsou aktivní po dobu trvání procesu.

  Objekty v generaci 2, které přežijí kolekce zůstávají v generaci 2, dokud nejsou určeny jako nedosažitelné v budoucí kolekci.

Uvolňování paměti dojít na konkrétní generace jako podmínky rozkaz. Shromažďování generace znamená shromažďování předmětů v této generaci a všech jejích mladších generacích. Uvolnění paměti generace 2 je také známé jako úplné uvolnění paměti, protože uvolňuje objekty ve všech generacích (to znamená, že všechny objekty ve spravované haldě).

### <a name="survival-and-promotions"></a>Přežití a propagace

Objekty, které nejsou uvolněny v uvolňování paměti jsou označovány jako survivors a jsou povýšeny na další generaci:

- Objekty, které přežijí uvolnění paměti generace 0, jsou povýšeny na generaci 1.
- Objekty, které přežijí uvolnění paměti generace 1 jsou povýšeny na generaci 2.
- Objekty, které přežijí uvolnění paměti generace 2, zůstávají v generaci 2.

Když systém uvolňování paměti zjistí, že míra přežití je vysoká v generaci, zvýší prahovou hodnotu přidělení pro toto generování. Další kolekce získá značnou velikost regenerované paměti. CLR neustále vyvažuje dvě priority: nenechat pracovní sadu aplikace příliš velké zpožděním uvolňování paměti a neumožňuje uvolnění paměti spustit příliš často.

### <a name="ephemeral-generations-and-segments"></a>Pomíjivé generace a segmenty

Protože objekty v generacích 0 a 1 jsou krátkodobé, tyto generace jsou známé jako *dočasné generace*.

Dočasné generace jsou přiděleny v segmentu paměti, který se označuje jako dočasný segment. Každý nový segment získaný systémem uvolňování paměti se stane novým dočasným segmentem a obsahuje objekty, které přežily uvolnění paměti generace 0. Starý dočasný segment se stává segmentem nové generace 2.

Velikost dočasného segmentu se liší v závislosti na tom, zda je systém 32bitový nebo 64bitový a na typu systému uvolňování paměti, který je spuštěn[(pracovní stanice nebo server GC](workstation-server-gc.md)). V následující tabulce jsou uvedeny výchozí velikosti dočasného segmentu.

|Pracovní stanice/server GC|32bitová|64bitová|
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

  - Omezení paměti na kontejneru.
  - Možnosti konfigurace [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) nebo [GCHeapHardLimitPercent.](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Systém uvolňování paměti používá následující informace k určení, zda jsou objekty aktivní:

- **Kořeny zásobníku**. Proměnné zásobníku poskytované kompilátorem just-in-time (JIT) a tchytačivým zásobníkem. Jit optimalizace můžete prodloužit nebo zkrátit oblasti kódu, ve kterém jsou hlášeny proměnné zásobníku do systému uvolňování paměti.

- **Popisovače uvolňování paměti**. Zpracovává, které odkazují na spravované objekty a které mohou být přiděleny podle uživatelského kódu nebo běžného jazyka runtime.

- **Statická data**. Statické objekty v aplikačních doménách, které mohou odkazovat na jiné objekty. Každá doména aplikace sleduje své statické objekty.

Před spuštěním uvolňování paměti jsou všechna spravovaná vlákna pozastavena s výjimkou vlákna, které spustilo uvolňování paměti.

Následující obrázek znázorňuje vlákno, které aktivuje uvolňování paměti a způsobí, že ostatní vlákna mají být pozastavena.

![Když vlákno aktivuje uvolňování paměti](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Nespravované prostředky

Pro většinu objektů, které aplikace vytvoří, můžete se spolehnout na uvolnění paměti automaticky provádět nezbytné úlohy správy paměti. Nespravované prostředky však vyžadují explicitní vyčištění. Nejběžnějším typem nespravovaného prostředku je objekt, který obtéká prostředek operačního systému, například popisovač souboru, popisovač okna nebo síťové připojení. Přestože systém uvolňování paměti je schopen sledovat životnost spravovaného objektu, který zapouzdřuje nespravovaný prostředek, nemá konkrétní znalosti o tom, jak vyčistit prostředek.

Při vytváření objektu, který zapouzdřuje nespravovaný prostředek, doporučujeme zadat potřebný kód `Dispose` k vyčištění nespravovaného prostředku ve veřejné metodě. Poskytnutím `Dispose` metody povolíte uživatelům objektu explicitně uvolnit jeho paměť po dokončení s objektem. Při použití objektu, který zapouzdřuje nespravovaný prostředek, ujistěte se, že volání `Dispose` podle potřeby.

Je také nutné poskytnout způsob, jak nespravované prostředky, které mají být `Dispose`uvolněny v případě, že spotřebitel vašeho typu zapomene volat . Můžete buď použít bezpečný popisovač k zalomení <xref:System.Object.Finalize?displayProperty=nameWithType> nespravovaného prostředku, nebo přepsat metodu.

Další informace o vyčištění nespravovaných prostředků naleznete v tématu [Vyčištění nespravovaných prostředků](unmanaged.md).

## <a name="see-also"></a>Viz také

- [Uvolňování paměti pracovní stanice a serveru](workstation-server-gc.md)
- [Uvolňování paměti na pozadí](background-gc.md)
- [Možnosti konfigurace pro gc](../../core/run-time-config/garbage-collector.md)
- [Uvolnění paměti](index.md)
