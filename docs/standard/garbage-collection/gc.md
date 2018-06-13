---
title: Kolekce paměti automatické správy a uvolňování paměti
description: Zjistěte, jak automatické paměti Správa je jedním ze služby, které poskytuje modul Common Language Runtime během spravovaného spouštění.
ms.date: 07/22/2016
ms.technology: dotnet-standard
ms.assetid: d095b0b6-2454-4e23-80b4-c9e8a447116c
ms.openlocfilehash: b9ce8b1fec5c6fc0808b86f06408c3f5d612e492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578141"
---
# <a name="automatic-memory-management-and-garbage-collection"></a>Kolekce paměti automatické správy a uvolňování paměti

Automatická správa paměti je jedním z služby, které poskytuje modul Common Language Runtime během spravovaného spouštění. Uvolňování paměti Common Language Runtime spravuje přidělování a uvolňování paměti pro aplikaci. Pro vývojáře to znamená, že nemáte napsat kód pro provedení paměti, že úlohy správy při vývoji spravované aplikace. Automatická správa paměti může eliminovat běžné problémy, jako je například zapomenutí volného objektu a způsobuje nevracení paměti nebo pokusu o přístup k paměti pro objekt, který již byl uvolněn. Tato část popisuje, jak má systém uvolňování přiděluje a uvolní paměť.

## <a name="allocating-memory"></a>Přidělování paměti

Při inicializaci nový proces modulu runtime vyhradí souvislou oblast adresního prostoru pro proces. Tento vyhrazené adresní prostor se nazývá spravovaná halda. Spravovaná halda uchovává ukazatel na adresu, kde se další objekt v haldě přidělí. Na začátku tento ukazatel je nastavena na spravovaná halda základní adresu. Spravovaná halda přidělovány všechny odkazové typy. Když aplikace vytvoří první typ odkazu, se přidělí paměť pro typ na základní adrese spravovaná halda. Aplikace vytvoří další objekt, bude systém uvolňování přidělí paměť pro něj v adresním prostoru, hned za první objekt. Tak dlouho, dokud adresní prostor je k dispozici, pokračuje uvolňování paměti k přidělení místa pro všechny nové objekty tímto způsobem.

Přidělování paměti ze spravované haldy je rychlejší než nespravované přidělování paměti. Modul runtime přidělí paměť pro objekt přidáním hodnoty do ukazatel, proto je téměř tak rychlý jako přidělování paměti ze zásobníku. Kromě toho nové objekty, které jsou alokovány postupně jsou uloženy souvisle ve spravované haldě, aplikace může přistupovat k objektům velmi rychle.

## <a name="releasing-memory"></a>Uvolňování paměti

Optimalizace engine systému uvolňování paměti určuje nejvhodnější čas k provedení v kolekci podle byla provedena alokace. Při uvolňování paměti provádí kolekce, uvolní paměť pro objekty, které jsou již používá aplikace. Určuje, které objekty jsou již používány zkoumáním kořenů aplikace. Každá aplikace má sadu kořenových certifikačních autorit. Kořenovém adresáři každého odkazuje na objekt v haldě spravované nebo je nastaven na hodnotu null. Kořeny aplikace zahrnout statických polí, místní proměnné a parametry v zásobníku podprocesu a registry procesoru. Uvolňování paměti má přístup k seznamu active kořeny, které udržují kompilátoru v běhu (JIT) a modulu runtime. Pomocí tohoto seznamu, prověří kořeny aplikace a v procesu vytvoří graf, který obsahuje všechny objekty, které jsou dostupné z kořenů.

Objekty, které nejsou v grafu nejsou dostupné z kořenů aplikace. Uvolňování paměti považuje nedostupný objekty paměti a vydá je paměť přidělená pro ně. V průběhu kolekce bude systém uvolňování prověří spravovaná halda hledá bloky adresního prostoru obsazené nedostupný objekty. Při zjišťování nedostupný objekt, používá funkci kopírování paměti kompaktních dosažitelné objekty v paměti, uvolnění bloky adresní prostory přidělené nedostupný objekty. Jakmile je paměť pro dosažitelné objekty byly komprimován, uvolňování paměti provede nezbytné korekce ukazatele tak, aby kořenů aplikace přejděte k objektům v jejich nová umístění. Spravovaná halda ukazatel také umístí po poslední dostupný objekt. Poznámka: Tento paměti se zkomprimuje pouze v případě, že kolekce zjistí velký počet objektů nedostupný. Pokud všechny objekty v haldě spravovaný přežijí sběr, není třeba pro komprimaci paměti.

Chcete-li zvýšit výkon, modul runtime přidělí paměť pro velké objekty v samostatné haldě. Uvolňování paměti automaticky uvolní paměť pro velké objekty. Nechcete-li přesouvání velkých objektů v paměti, ale není zkomprimovanou tuto paměť.

## <a name="generations-and-performance"></a>Generace a výkon

Za účelem optimalizace výkonu systému uvolňování spravovaná halda je rozdělené do tří generací: 0, 1 a 2. Modul runtime paměti kolekce algoritmus je založena na několik generalizace, které zjistí počítač softwarového oboru na hodnotu true, a experimentování se uvolňování paměti kolekci schémat. Nejprve je rychlejší compact paměti pro část spravovaná halda než pro celý spravovaná halda. Za druhé novější objekty budou mít kratší životnost a starší objekty budou mít delší životnost. Nakonec novější objekty často vzájemně souvisí a získat přístup k aplikací přibližně ve stejnou dobu.

Modul runtime systém uvolňování paměti ukládá nové objekty v 0. generace. Objekty vytvořené dříve v životního cyklu aplikace, které zůstanou platné i po kolekce jsou povýší a uložené v generace 1 a 2. Proces povýšení objekt je popsán dále v tomto tématu. Protože je rychlejší kompaktních část spravovaná halda než celou haldu, toto schéma umožňuje uvolňování paměti uvolnit paměť v konkrétní generování než uvolnit paměť pro celý spravovaná halda pokaždé, když provádí kolekce.

Ve skutečnosti provádí garbage collector v kolekci při zaplnění generace 0. Pokud se aplikace pokusí vytvořit nový objekt při zaplnění generace 0, uvolňování paměti zjistí se žádná adresa zbývající prostor v generace 0 přidělení pro objekt. Uvolňování paměti provádí kolekce ve snaze volné místo na adresu v generace 0 pro objekt. Uvolňování paměti začne prověřením objektů v generace 0 a nikoli všech objektů v spravovaná halda. Toto je nejvhodnější přístup, protože nové objekty mívají k krátkou životnost a očekává se, že mnoho objektů v generace 0 již nebude používán aplikací při provádění kolekce. Kromě toho kolekce samotné generace 0 často získá dostatek paměti pro umožňuje aplikaci pokračovat ve vytváření nových objektů.

Po uvolňování paměti provádí sběr generace 0, zkomprimuje paměť pro dosažitelné objekty jak je popsáno v [uvolňování paměti](#releasing-memory) výše v tomto tématu. Uvolňování paměti potom povýší tyto objekty a považuje tuto část spravovaná halda generace 1. Protože objekty, které zůstanou platné i po kolekce mívají k delší životnost, má smysl povýšit je vyšší generace. Uvolňování paměti v důsledku toho není nutné přezkoumat objekty v generace 1 a 2 pokaždé, když provádí sběr generace 0.

Po uvolňování provede jeho první kolekce generace 0 a zvýší úroveň dostupné objekty, které se 1. generace, považuje zbytek spravovaná halda generace 0. Nadále přidělit paměť pro nové objekty v 0. generace, dokud zaplnění generace 0 a je nutné provést jiné kolekce. Optimalizace engine systému uvolňování paměti v tomto okamžiku Určuje, zda je potřebné k prozkoumání objektů v starší generace. Například pokud sběr generace 0 nezíská dostatek paměti pro aplikace úspěšně dokončit pokus vytvořit nový objekt, bude systém uvolňování provést sběr generace 1, pak generace 2. Pokud to nezíská dostatek paměti, bude systém uvolňování provést kolekce generace 2, 1 nebo 0. Po každé kolekce uvolňování zkomprimuje dosažitelné objekty v generace 0 a povýší je 1. generace. Objekty v 1. generace, které zůstanou platné i po kolekce povýšené na 2. generace. Protože uvolňování podporuje jenom tři generace, zůstanou objekty v 2. generace, které zůstanou platné i po kolekce v 2. generace, dokud jsou určeny k není k dispozici v budoucí kolekci.

## <a name="releasing-memory-for-unmanaged-resources"></a>Uvolňování paměti pro nespravované prostředky

Pro většinu objektů, které vytváří vaše aplikace můžete spolehnout na uvolňování automaticky provádět úlohy správy paměti. Nicméně nespravované prostředky vyžadují explicitní vyčištění. Nejběžnějším typem nespravovaných prostředků je objekt, který zabalí prostředek operačního systému, například popisovač souboru, popisovač okna nebo síťové připojení. I když bude systém uvolňování je schopný sledovat životnost spravovaného objektu, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak vyčistit prostředku. Když vytvoříte objekt, který zapouzdřuje nespravovaný prostředek, doporučujeme zadat kód nezbytné k vyčištění nespravovaný prostředek veřejné `Dispose` metoda. Tím, že poskytuje `Dispose` metoda, povolíte uživatelům objektu explicitně uvolnit jeho paměť po ukončení práce s daným objektem. Použijete-li objekt, který zapouzdřuje nespravovaný prostředek, byste měli vědět o `Dispose` a pojmenujte ji podle potřeby. Další informace o čištění nespravovaných prostředků a příklad tohoto vzoru návrhu pro implementaci `Dispose`, najdete v části [uvolňování paměti v rozhraní .NET](index.md).

## <a name="see-also"></a>Viz také

[System.GC](xref:System.GC)

[Uvolňování paměti v rozhraní .NET](index.md)

