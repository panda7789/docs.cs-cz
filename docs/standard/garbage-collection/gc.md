---
title: Automatická správa paměti a uvolňování paměti
description: Zjistěte, jak je automatická správa paměti jednou ze služeb, které poskytuje common language runtime během spravovaného spuštění.
ms.date: 07/22/2016
ms.technology: dotnet-standard
ms.assetid: d095b0b6-2454-4e23-80b4-c9e8a447116c
ms.openlocfilehash: 8046cb744dccaf512208d517c243640820efce8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61945363"
---
# <a name="automatic-memory-management-and-garbage-collection"></a>Automatická správa paměti a uvolňování paměti

Automatická správa paměti je jednou ze služeb, které poskytuje common language runtime během spravovaného spuštění. Uvolňování paměti v běžném jazyce spravuje přidělení a uvolnění paměti pro aplikaci. Pro vývojáře to znamená, že není třeba psát kód k provádění úloh správy paměti při vývoji spravovaných aplikací. Automatická správa paměti může eliminovat běžné problémy, jako je například zapomínání na uvolnění objektu a příčinou nevracení paměti nebo pokusu o přístup k paměti pro objekt, který již byl uvolněn. Tato část popisuje, jak systém uvolňování paměti přiděluje a uvolňuje paměť.

## <a name="allocating-memory"></a>Přidělování paměti

Při inicializaci nového procesu si zaběhu rezervuje souvislou oblast adresního prostoru pro proces. Tento vyhrazený adresní prostor se nazývá spravovaná halda. Spravovaná halda udržuje ukazatel na adresu, kde bude přidělen další objekt v haldě. Zpočátku tento ukazatel je nastavena na základní adresu spravované haldy. Všechny typy odkazů jsou přiděleny na spravované haldy. Když aplikace vytvoří první typ odkazu, je přidělena paměť pro typ na základní adrese spravované haldy. Když aplikace vytvoří další objekt, systém uvolňování paměti pro něj přiděluje paměť v adresním prostoru bezprostředně za prvním objektem. Tak dlouho, dokud adresní prostor je k dispozici, systém uvolňování paměti nadále přidělovat prostor pro nové objekty tímto způsobem.

Přidělení paměti ze spravované haldy je rychlejší než přidělení nespravované paměti. Vzhledem k tomu, že runtime přiděluje paměť pro objekt přidáním hodnoty k ukazateli, je téměř stejně rychlý jako přidělení paměti ze zásobníku. Navíc vzhledem k tomu, že nové objekty, které jsou přiděleny postupně jsou uloženy souvislé ve spravované haldě, aplikace může přistupovat k objektům velmi rychle.

## <a name="releasing-memory"></a>Uvolnění paměti

Optimalizační modul systému uvolňování paměti určuje nejlepší čas k provedení kolekce na základě provedených přidělení. Když systém uvolňování paměti provádí kolekci, uvolní paměť pro objekty, které již nejsou používány aplikací. Určuje, které objekty se již nepoužívají zkoumáním kořenů aplikace. Každá aplikace má sadu kořenů. Každý kořen odkazuje na objekt na spravované haldě nebo je nastavenna na hodnotu null. Kořeny aplikace zahrnují statická pole, místní proměnné a parametry v zásobníku vlákna a registry procesoru. Systém uvolňování paměti má přístup k seznamu aktivních kořenů, které kompilátor just-in-time (JIT) a za běhu udržují. Pomocí tohoto seznamu zkoumá kořeny aplikace a v procesu vytvoří graf, který obsahuje všechny objekty, které jsou dosažitelné z kořenů.

Objekty, které nejsou v grafu jsou nedostupné z kořenů aplikace. Systém uvolňování paměti považuje nedosažitelné objekty za nesmyslné a uvolní paměť, která je pro ně přidělena. Během kolekce systém uvolňování paměti zkoumá spravované haldy, hledá bloky adresního prostoru obsazené nedosažitelné objekty. Při zjišťování každého nedosažitelného objektu používá funkci kopírování paměti k komprimaci dosažitelných objektů v paměti a uvolňuje bloky adresních prostorů přidělených nedostupným objektům. Jakmile paměť pro dosažitelné objekty byla zkomprimována, systém uvolňování paměti provede potřebné opravy ukazatele tak, aby kořeny aplikace odkazují na objekty v jejich nových umístěních. Také umístí ukazatele spravované haldy za poslední dosažitelný objekt. Všimněte si, že paměť je komprimována pouze v případě, že kolekce zjistí významný počet nedostupných objektů. Pokud všechny objekty ve spravované haldy přežít kolekce, pak není nutné pro zhutňování paměti.

Chcete-li zlepšit výkon, runtime přiděluje paměť pro velké objekty v samostatné haldy. Systém uvolňování paměti automaticky uvolní paměť pro velké objekty. Chcete-li se však vyhnout přesouvání velkých objektů v paměti, tato paměť není komprimována.

## <a name="generations-and-performance"></a>Generace a výkon

Chcete-li optimalizovat výkon systému uvolňování paměti, je spravovaná halda rozdělena do tří generací: 0, 1 a 2. Algoritmus uvolňování paměti za běhu je založen na několika generalizacích, které odvětví počítačového softwaru zjistilo, že je pravdivé experimentováním se schématy uvolňování paměti. Nejprve je rychlejší komprimovat paměť pro část spravované haldy než pro celou spravovanou haldu. Za druhé, novější objekty budou mít kratší životnost a starší objekty budou mít delší životnost. Nakonec novější objekty mají tendenci být vzájemně propojeny a přistupovat k nim přibližně ve stejnou dobu.

Uvolňování času runtime ukládá nové objekty v generaci 0. Objekty vytvořené v rané fázi životnosti aplikace, které přežijí kolekce jsou povýšeny a uloženy v generacích 1 a 2. Proces propagace objektu je popsán dále v tomto tématu. Vzhledem k tomu, že je rychlejší komprimovat část spravované haldy než celou haldu, toto schéma umožňuje uvolňování paměti v určité generaci, nikoli uvolnění paměti pro celou spravovanou haldu pokaždé, když provádí kolekci.

Ve skutečnosti systém uvolňování paměti provádí kolekci při generování 0 je plná. Pokud se aplikace pokusí vytvořit nový objekt při generování 0 je plná, systém uvolňování zjistí, že neexistuje žádný adresní prostor zbývající v generaci 0 přidělit pro objekt. Systém uvolňování paměti provádí kolekci ve snaze uvolnit adresní prostor v generaci 0 pro objekt. Uvolňování začíná zkoumáním objektů v generaci 0, nikoli všechny objekty ve spravované haldě. Toto je nejúčinnější přístup, protože nové objekty mají tendenci mít krátkou životnost a očekává se, že mnoho objektů v generaci 0 již nebude používáno aplikací při provádění kolekce. Kromě toho kolekce generace 0 sám často uvolní dostatek paměti, aby aplikace pokračovat ve vytváření nových objektů.

Po uvolňování provede kolekci generace 0, zkomprimuje paměť pro dosažitelné objekty, jak je vysvětleno v [uvolnění paměti](#releasing-memory) dříve v tomto tématu. Systém uvolňování paměti pak podporuje tyto objekty a považuje tuto část spravované haldy generace 1. Protože objekty, které přežívají kolekce mají tendenci mít delší životnost, má smysl je povýšit na vyšší generaci. V důsledku toho systém uvolňování paměti nemusí znovu prozkoumat objekty v generacích 1 a 2 pokaždé, když provede kolekci generace 0.

Po uvolňování provede jeho první kolekce generace 0 a podporuje dosažitelné objekty generace 1, považuje zbytek spravované haldy generace 0. Nadále přidělovat paměť pro nové objekty v generaci 0 až generace 0 je plná a je nutné provést jinou kolekci. V tomto okamžiku optimalizační modul systému uvolňování paměti určuje, zda je nutné prozkoumat objekty ve starších generacích. Například pokud kolekce generace 0 nezíská dostatek paměti pro aplikaci úspěšně dokončit svůj pokus o vytvoření nového objektu, systém uvolňování paměti může provést kolekci generace 1, pak generace 2. Pokud to není uvolnění dostatek paměti, systém uvolňování paměti můžete provést kolekci generace 2, 1 a 0. Po každé kolekci systém uvolňování zkomprimuje dosažitelné objekty v generaci 0 a povýší je na generaci 1. Objekty v generaci 1, které přežijí kolekce jsou povýšeny na generaci 2. Vzhledem k tomu, že systém uvolňování paměti podporuje pouze tři generace, objekty v generaci 2, které přežijí kolekci, zůstávají v generaci 2, dokud nebudou určeny jako nedosažitelné v budoucí kolekci.

## <a name="releasing-memory-for-unmanaged-resources"></a>Uvolnění paměti pro nespravované prostředky

Pro většinu objektů, které vaše aplikace vytvoří, můžete se spolehnout na uvolňování automaticky provádět nezbytné úlohy správy paměti. Nespravované prostředky však vyžadují explicitní vyčištění. Nejběžnějším typem nespravovaného prostředku je objekt, který obtéká prostředek operačního systému, například popisovač souboru, popisovač okna nebo síťové připojení. Přestože systém uvolňování paměti je schopen sledovat životnost spravovaného objektu, který zapouzdřuje nespravovaný prostředek, nemá konkrétní znalosti o tom, jak vyčistit prostředek. Při vytváření objektu, který zapouzdřuje nespravovaný prostředek, doporučujeme zadat potřebný kód `Dispose` k vyčištění nespravovaného prostředku ve veřejné metodě. Poskytnutím `Dispose` metody povolíte uživatelům objektu explicitně uvolnit jeho paměť po dokončení s objektem. Při použití objektu, který zapouzdřuje nespravovaný prostředek, měli byste si být vědomi `Dispose` a volat podle potřeby. Další informace o vyčištění nespravovaných prostředků a příklad `Dispose`návrhového vzoru pro implementaci naleznete [v tématu Uvolňování paměti v rozhraní .NET](index.md).

## <a name="see-also"></a>Viz také

- [System.GC](xref:System.GC)
- [Uvolňování paměti v rozhraní .NET](index.md)
