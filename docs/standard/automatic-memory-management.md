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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e80e524a8bac28195067ce6bd30504005fc4b5a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698912"
---
# <a name="automatic-memory-management"></a>Automatická správa paměti
Automatická správa paměti je jedna ze služeb, které poskytuje modul Common Language Runtime během [Managed Execution](../../docs/standard/managed-execution-process.md). Modul Common Language Runtime systému uvolňování paměti spravuje přidělování a uvolňování paměti pro aplikaci. Pro vývojáře to znamená, že není nutné napsat kód k provedení paměti, že se úlohy správy počítačů při vývoji spravované aplikace. Automatická správa paměti může eliminovat běžné problémy, jako je například zapomínání uvolnění objektu a způsobuje nevrácení paměti nebo pokusu o přístup k paměti pro objekt, který již byl uvolněn. Tato část popisuje, jak systému uvolňování paměti přiděluje a uvolňuje paměť.  
  
## <a name="allocating-memory"></a>Přidělování paměti  
 Při inicializaci nový proces, modul runtime rezervuje souvislé oblastí adresního prostoru procesu. Tato vyhrazeného adresního prostoru se nazývá spravovaná halda. Spravovaná halda uchovává ukazatel na adresu, kde bude přidělena další objekt v haldě. This – ukazatel na začátku je nastavena na spravované haldě základní adresa. Všechny [referenční typy](../../docs/standard/base-types/common-type-system.md) jsou přidělovány na spravované haldě. Pokud aplikace vytvoří první typ odkazu, je paměť přidělena typu spravované haldě na základní adrese. Aplikace vytvoří další objekt, systému uvolňování paměti přiděluje paměť pro něj v adresním prostoru, hned za první objekt. Adresní prostor je k dispozici, pokračuje v systému uvolňování paměti k přidělení místa pro nové objekty tímto způsobem.  
  
 Přidělování paměti ze spravované haldy je rychlejší než nespravovanou paměť přidělení. Vzhledem k tomu, že modul runtime přiděluje paměť pro objekt přidáním hodnoty na ukazatel, je skoro tak rychle jako přidělování paměti ze zásobníku. Navíc vzhledem k tomu, že nové objekty, které jsou přiděleny po sobě jdoucích jsou uložena souvisle ve spravované haldě, aplikace může přístup k objektům velmi rychle.  
  
<a name="cpconautomaticmemorymanagementreleasingmemoryanchor1"></a>   
## <a name="releasing-memory"></a>Uvolňování paměti  
 Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění podle přidělení prováděné. Když uvolňování paměti provede kolekce, uvolní paměť pro objekty, které jsou již nejsou déle používány aplikací. Určuje, které objekty jsou již nejsou déle používány prozkoumáním kořenů aplikace. Každá aplikace má sadu kořenových adresářů. Kořenovém adresáři každého odkazuje na objekt na spravované haldě nebo je nastaven na hodnotu null. Kořeny aplikace zahrnují statická pole, místní proměnné a parametry v zásobníku vlákna a registruje procesor. Uvolňování paměti má přístup k seznamu aktivní kořenových adresářů, který [kompilátor just-in-time (JIT)](../../docs/standard/managed-execution-process.md) a udržovat modulu runtime. Pomocí tohoto seznamu, prověří kořeny aplikace a vytvoří graf, který obsahuje všechny objekty, které jsou dostupné z kořenů v procesu.  
  
 Objekty, které nejsou v grafu jsou dostupná z kořenové adresáře aplikace. Uvolňování paměti bere v úvahu nedostupné objekty uvolnění paměti a vydá je paměť přidělená pro ně. Během shromažďování uvolňování prozkoumá spravované haldě, hledají adresní prostor obsazena nedostupné objekty. Jako nedostupný objekt zjistí, používá funkci kopírování paměti ke komprimaci dostupný objektů v paměti se bloky adresní prostory, které jsou přiděleny do nedostupný objektů. Jakmile setřepána paměť pro dostupné objekty, uvolňování paměti provede opravy nutné ukazatel tak, aby aplikace kořeny odkazují na objekty v jejich novém umístění. Také umístí spravované haldě ukazatel po poslední dostupný objekt. Všimněte si že paměť je komprimovat pouze v případě, že zjistí velký počet nedostupné objekty kolekce. Pokud všechny objekty ve spravované haldě překonání kolekci, není nutné pro komprimaci paměti.  
  
 Pokud chcete zlepšit výkon, modul runtime přiděluje paměť pro velké objekty v samostatných haldy. Uvolňování paměti automaticky uvolní paměť pro velké objekty. Abyste se vyhnuli přenášení velkých objektů v paměti, ale tato paměť není setřepána.  
  
## <a name="generations-and-performance"></a>Generace a výkon  
 Za účelem optimalizace výkonu systému uvolňování paměti spravované haldy rozdělen na tři generace: 0, 1 a 2. Modul runtime uvolňování paměti kolekce algoritmus je založená na několik generalizace, které softwarovém průmyslu počítač objevil na hodnotu true Experimentováním s uvolňování paměti kolekce schémat. Nejprve je rychlejší ke komprimaci paměti pro část spravované haldy než pro celou spravovanou haldu. Za druhé novější objekty se mají životnost kratší a starší objekty se mají delší životnost. A konečně, novější objekty mají tendenci vzájemně souvisí a přistupuje aplikace přibližně ve stejnou dobu.  
  
 Modul runtime systému uvolňování paměti uloží nové objekty 0. generace. Objekty vytvořené v rané fázi životního cyklu aplikace, které byly zachovány při kolekce jsou povýšeny a uloženy v generace 1 a 2. Proces povýšení objektu je popsána dále v tomto tématu. Protože je rychlejší compact část spravované haldy než celý haldy, toto schéma umožňuje uvolňování paměti uvolní paměť při konkrétní generování spíše než uvolnění paměti pro celou spravovanou haldu pokaždé, když provádí kolekce.  
  
 Ve skutečnosti provádí systému uvolňování paměti kolekce při zaplnění 0. generace. Pokud se aplikace pokusí vytvořit nový objekt při zaplnění 0. generace, uvolňování paměti zjistí, že neexistuje žádný adresní prostor zbývajících v generaci 0 pro přidělení objektu. Uvolňování paměti kolekce provádí při pokusu o uvolnění adresní prostor v generaci 0 pro objekt. Uvolňování paměti spustí porovnáním objektů v generaci 0, ne všechny objekty ve spravované haldě. Toto je nejefektivnější postup vzhledem k tomu, že nové objekty jsou obvykle krátkou životnost a očekává se, že mnoho objektů v generaci 0 již nebude používán aplikací při kolekce se provádí. Sběr generace 0 samostatně navíc uvolňuje často dostatek paměti, aby aplikace mohla pokračovat ve vytváření nových objektů.  
  
 Po uvolňování paměti provádí sběr generace 0, komprimuje paměť pro dostupné objekty jak je vysvětleno v [uvolňování paměti](#cpconautomaticmemorymanagementreleasingmemoryanchor1) výše v tomto tématu. Uvolňování paměti pak podporuje tyto objekty a bere v úvahu tuto část 1. generace spravované haldě. Protože objekty, které byly zachovány při kolekce jsou často mají delší životnost, má smysl pro povýšení na vyšší generace. Uvolňování paměti v důsledku toho není nutné prozkoumat objekty v generacích 1 a 2 pokaždé, když provádí sběr generace 0.  
  
 Poté, co systému uvolňování paměti provede jeho první kolekce generace 0 a podporuje dostupné objekty do 1. generace, bude považovat za zbývající spravované haldě generace 0. Pokračuje se přidělit paměť pro nové objekty v generaci 0 až 0. generace je plný a je potřeba provést jiné kolekce. Optimalizující modul systému uvolňování paměti v tomto okamžiku Určuje, zda je nutné prozkoumat objekty v generacích starší. Například pokud kolekce generace 0 nezíská dostatek paměti pro aplikaci pro úspěšné dokončení jeho pokusu o vytvoření nového objektu, můžete provádět systému uvolňování paměti kolekce generace 1 a pak 2. generace. Pokud to nezíská dostatek paměti, můžete provádět systému uvolňování paměti kolekce generace 2 a 1, 0. Za každou kolekci systému uvolňování paměti komprimuje dostupné objekty v generaci 0 a podporuje je 1. generace. Objekty v 1. generace, které byly zachovány při kolekce jsou povýšeny do generace 2. Protože systému uvolňování paměti se podporuje jenom tři generace, objekty v 2. generace, které byly zachovány při kolekci zůstanou v generaci 2, dokud se určují nedostupná v budoucnu kolekci.  
  
## <a name="releasing-memory-for-unmanaged-resources"></a>Uvolňování paměti pro nespravované prostředky  
 U většiny objektů, které vytváří vaše aplikace můžete se spolehnout na uvolňování paměti automaticky provádět úlohy správy dost paměti. Nespravované prostředky však vyžaduje explicitní vyčištění. Nejběžnějším typem nespravovaného prostředku je objekt, který obaluje prostředek operačního systému, například popisovač souboru, popisovač okna nebo připojení k síti. I když uvolňování paměti je schopen sledovat dobu života spravovaný objekt, který zapouzdřuje nespravovaný prostředek, nemá specifické znalosti o tom, jak prostředek vyčistit. Při vytváření objektu, který zapouzdřuje nespravovaný prostředek, doporučuje se, že zadáte potřebný kód pro vyčištění nespravovaných prostředků ve veřejném **Dispose** metody. Tím, že poskytuje **Dispose** metoda, povolíte uživatelům objektu explicitně uvolnit jeho paměti po ukončení práce s objektem. Použijete-li objekt, který zapouzdřuje nespravovaný prostředek, byste měli vědět **Dispose** a volejte jej podle potřeby. Další informace o vyčištění nespravovaných prostředků a tu je ukázka návrhový vzor pro implementování **Dispose**, naleznete v tématu [uvolňování](../../docs/standard/garbage-collection/index.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.GC>
- [Uvolňování paměti](../../docs/standard/garbage-collection/index.md)
- [Proces spravovaného spuštění](../../docs/standard/managed-execution-process.md)
