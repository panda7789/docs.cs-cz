---
title: Automatická správa paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, automatic memory management
- memory, allocating
- memory, automatic memory management
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- managed heap
- runtime, automatic memory management
ms.assetid: d4850de5-fa63-4936-a250-5678d118acba
ms.openlocfilehash: d112bf6d145893bd7b0f99e2b233fc83e72fe227
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140567"
---
# <a name="automatic-memory-management"></a>Automatická správa paměti
Automatická správa paměti je jednou ze služeb, které modul CLR (Common Language Runtime) poskytuje během [spravovaného spuštění](../../docs/standard/managed-execution-process.md). Systém uvolňování paměti modulu CLR (Common Language Runtime) spravuje přidělování a uvolňování paměti pro aplikaci. Pro vývojáře to znamená, že nemusíte psát kód pro provádění úloh správy paměti při vývoji spravovaných aplikací. Automatická správa paměti může eliminovat běžné problémy, například forgetting k uvolnění objektu a příčinou nevrácení paměti nebo pokusu o přístup k paměti pro objekt, který již byl uvolněn. Tato část popisuje, jak systém uvolňování paměti přiděluje a uvolňuje paměť.  
  
## <a name="allocating-memory"></a>Přidělování paměti  
 Při inicializaci nového procesu vyhradí modul runtime souvislou oblast adresního prostoru pro daný proces. Tento vyhrazený adresní prostor se nazývá spravovaná halda. Spravovaná halda udržuje ukazatel na adresu, kde bude přidělen další objekt v haldě. Zpočátku je tento ukazatel nastavený na základní adresu spravované haldy. Všechny [typy odkazů](../../docs/standard/base-types/common-type-system.md) jsou přiděleny na spravovanou haldu. Když aplikace vytvoří první typ odkazu, přidělí se paměť pro typ na základní adrese spravované haldy. Když aplikace vytvoří další objekt, systém uvolňování paměti přidělí paměť v adresním prostoru hned za prvním objektem. Pokud je k dispozici adresní prostor, uvolňování paměti pro nové objekty tímto způsobem stále přiděluje místo.  
  
 Přidělování paměti ze spravované haldy je rychlejší než nespravované přidělení paměti. Vzhledem k tomu, že modul Runtime přiděluje paměť pro objekt přidáním hodnoty k ukazateli, je téměř stejně rychlá jako přidělování paměti ze zásobníku. Kromě toho vzhledem k tomu, že nové objekty, které jsou přiděleny po sobě, jsou uloženy souvisle ve spravované haldě, aplikace může přistupovat k objektům velmi rychle.  
  
<a name="cpconautomaticmemorymanagementreleasingmemoryanchor1"></a>   
## <a name="releasing-memory"></a>Uvolňování paměti  
 Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení kolekce na základě přidělení. Když systém uvolňování paměti provede kolekci, uvolní paměť pro objekty, které již aplikace nepoužívá. Určuje, které objekty již nejsou používány, prozkoumáním kořenů aplikace. Každá aplikace má sadu kořenů. Každý kořenový adresář buď odkazuje na objekt na spravované haldě, nebo je nastaven na hodnotu null. Kořeny aplikace zahrnují statická pole, místní proměnné a parametry v zásobníku vlákna a Registry procesoru. Systém uvolňování paměti má přístup k seznamu aktivních kořenových adresářů, které [kompilátor JIT (just-in-time)](../../docs/standard/managed-execution-process.md) a modul runtime udržují. Pomocí tohoto seznamu prohlíží kořeny aplikace a v procesu vytvoří graf, který obsahuje všechny objekty, které jsou dostupné z kořenů.  
  
 Objekty, které nejsou v grafu, jsou nedosažitelné z kořenů aplikace. Systém uvolňování paměti považuje nedosažitelné objekty za paměti a uvolní přidělenou paměť. V průběhu kolekce systém uvolňování paměti ověřuje spravovanou haldu a hledá bloky adresního prostoru obsazené nedosažitelnými objekty. Vzhledem k tomu, že zjistí každý nedosažitelný objekt, používá funkci kopírování paměti pro komprimaci dosažitelných objektů v paměti a uvolní bloky adresních prostorů přidělených nedostupným objektům. Po komprimaci paměti pro dostupné objekty provede systém uvolňování paměti nezbytné opravy ukazatelů, aby kořeny aplikace odkazovaly na objekty v jejich nových umístěních. Také umístí ukazatel spravované haldy za poslední dosažitelný objekt. Všimněte si, že paměť je komprimována pouze v případě, že kolekce zjistí významný počet nedosažitelných objektů. Pokud všechny objekty ve spravované haldě přestanou kolekci, nepotřebujete komprimaci paměti.  
  
 Za účelem zvýšení výkonu přiděluje modul runtime paměť pro velké objekty v samostatné haldě. Systém uvolňování paměti automaticky uvolňuje paměť pro velké objekty. Chcete-li však zabránit přesunutí velkých objektů do paměti, Tato paměť není komprimována.  
  
## <a name="generations-and-performance"></a>Generace a výkon  
 Pro optimalizaci výkonu uvolňování paměti je spravovaná halda rozdělená na tři generace: 0, 1 a 2. Algoritmus uvolňování paměti modulu runtime je založen na několika generalizech, které zjistila, že počítač softwarového softwaru je pravdivý, a to experimentováním se schématy uvolňování paměti. Nejdřív je rychlejší komprimace paměti pro část spravované haldy, než pro celou spravovanou haldu. Za druhé budou novější objekty kratší životnost a starší objekty budou mít delší životnost. A konečně, novější objekty by měly být vzájemně vzájemně propojené a k nim budou mít k dispozici aplikace přibližně stejnou dobu.  
  
 Systém uvolňování paměti modulu runtime ukládá nové objekty v generaci 0. Objekty vytvořené na začátku v životním cyklu aplikace, které jsou převedené na kolekce, jsou povýšeny a uloženy v generacích 1 a 2. Proces povýšení objektu je popsán dále v tomto tématu. Vzhledem k tomu, že je rychlejší komprimovat část spravované haldy, než je celá halda, toto schéma umožňuje uvolňování paměti uvolnit paměť v konkrétní generaci místo uvolnění paměti pro celou spravovanou haldu pokaždé, když aplikace provede kolekci.  
  
 Ve skutečnosti systém uvolňování paměti provede kolekci, pokud je generace 0 plná. Pokud se aplikace pokusí vytvořit nový objekt, když je generace 0 plná, zjistí systém uvolňování paměti, že v generaci 0 není zbývající adresní prostor pro přidělení objektu. Systém uvolňování paměti provede kolekci v pokusu o uvolnění adresního prostoru v generaci 0 pro daný objekt. Systém uvolňování paměti začíná prozkoumáním objektů v generaci 0 místo všech objektů ve spravované haldě. Jedná se o nejúčinnější přístup, protože nové objekty mají krátkou životnost a očekává se, že celá řada objektů v generaci 0 již nebude aplikací používána při provádění kolekce. Kromě toho kolekce samotné generace 0 často uvolňuje dostatek paměti, aby aplikace mohla pokračovat v vytváření nových objektů.  
  
 Jakmile systém uvolňování paměti provede kolekci generace 0, zkomprimuje paměť pro dosažitelné objekty, jak je vysvětleno v části [uvolnění paměti](#cpconautomaticmemorymanagementreleasingmemoryanchor1) dříve v tomto tématu. Systém uvolňování paměti pak propaguje tyto objekty a vezme v úvahu tuto část spravované haldy 1. generace. Vzhledem k tomu, že objekty, které zachují kolekce, mají obvykle delší životnost, je vhodné je zvýšit na vyšší generaci. V důsledku toho systém uvolňování paměti nemusí znovu prošetřit objekty v generacích 1 a 2 pokaždé, když provede kolekci generace 0.  
  
 Poté, co systém uvolňování paměti provede první kolekci generace 0 a propaguje dosažitelné objekty na generaci 1, považuje to za zbytek spravované haldy 0. Nadále přiděluje paměť pro nové objekty v generaci 0, dokud není generace 0 plná a je nutné provést jinou kolekci. V této fázi optimalizující modul systému uvolňování paměti určuje, zda je nutné prošetřit objekty ve starších generacích. Například pokud kolekce generace 0 neuvolní dostatek paměti pro aplikaci k úspěšnému dokončení svého pokusu o vytvoření nového objektu, systém uvolňování paměti může provést kolekci 1. generace, pak 2. generace. Pokud to neuvolní dostatek paměti, může systém uvolňování paměti provést kolekci generací 2, 1 a 0. Po každé kolekci systém uvolňování paměti zkomprimuje dostupné objekty v generaci 0 a propaguje je na generaci 1. Objekty v generaci 1, které dodržely kolekce, jsou povýšeny na generaci 2. Vzhledem k tomu, že systém uvolňování paměti podporuje pouze tři generace, objekty v generaci 2, které přestanou kolekci, zůstávají v generaci 2, dokud nebudou v budoucí kolekci nedostupné.  
  
## <a name="releasing-memory-for-unmanaged-resources"></a>Uvolnění paměti pro nespravované prostředky  
 Pro většinu objektů, které vaše aplikace vytvoří, můžete spoléhat na systém uvolňování paměti, aby automaticky prováděla nezbytné úlohy správy paměti. Nespravované prostředky však vyžadují explicitní vyčištění. Nejběžnějším typem nespravovaného prostředku je objekt, který balí prostředek operačního systému, jako je například popisovač souboru, popisovač okna nebo síťové připojení. I když je systém uvolňování paměti schopný sledovat životnost spravovaného objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak prostředek vyčistit. Při vytváření objektu, který zapouzdřuje nespravovaný prostředek, se doporučuje zadat potřebný kód pro vyčištění nespravovaného prostředku ve veřejné metodě **Dispose** . Poskytnutím metody **Dispose** umožníte uživatelům vašeho objektu explicitně uvolnit svou paměť, až se dokončí s objektem. Při použití objektu, který zapouzdřuje nespravovaný prostředek, byste měli být vědomi **Dispose** a zavolat ho podle potřeby. Další informace o čištění nespravovaných prostředků a příklad vzoru návrhu pro implementaci **Dispose**naleznete v tématu [uvolňování paměti](../../docs/standard/garbage-collection/index.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC>
- [Uvolňování paměti](../../docs/standard/garbage-collection/index.md)
- [Proces spravovaného spuštění](../../docs/standard/managed-execution-process.md)
