---
title: Provádění aritmetických operací s daty a časy
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344173"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Provádění aritmetických operací s daty a časy

Přestože <xref:System.DateTime> i <xref:System.DateTimeOffset> struktury poskytují členy, které provádějí aritmetické operace na jejich hodnoty, výsledky aritmetické operace jsou velmi odlišné. Toto téma zkoumá tyto rozdíly, spojuje je s stupňů povědomí o časovém pásmu v datech a čase dat a popisuje, jak provádět plně operace s ohledem na časové pásmo pomocí data a času data.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porovnání a aritmetické operace s hodnotami DateTime

Vlastnost <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> umožňuje <xref:System.DateTimeKind> hodnotu, která má být přiřazena k datu a času k označení, zda představuje místní čas, koordinovaný světový čas (UTC) nebo čas v neurčeném časovém pásmu. Tyto informace o omezeném časovém pásmu jsou však ignorovány při <xref:System.DateTimeKind> porovnávání nebo provádění aritmetiky data a času na hodnoty. Následující příklad, který porovnává aktuální místní čas s aktuálníčas UTC, ilustruje toto.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

Metoda <xref:System.DateTime.CompareTo%28System.DateTime%29> hlásí, že místní čas je dřívější než (nebo menší než) čas UTC a operace odčítání označuje, že rozdíl mezi Čas emIt a místním časem pro systém v americkém tichomořském standardním časovém pásmu je sedm hodin. Ale protože tyto dvě hodnoty poskytují různé reprezentace jednoho bodu v čase, je jasné, v tomto případě, že časový interval je zcela připsat posun místního časového pásma od Času UTC.

Obecněji, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nemá vliv na <xref:System.DateTime.Kind> výsledky vrácené porovnání a aritmetické metody (jako srovnání dvou identických bodů v čase naznačuje), i když může ovlivnit interpretaci těchto výsledků. Například:

- Výsledek jakékoli aritmetické operace provedené na dvou <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotách <xref:System.DateTimeKind> data a času, jejichž vlastnosti se rovnají, odráží skutečný časový interval mezi těmito dvěma hodnotami. Podobně porovnání dvou těchto hodnot data a času přesně odráží vztah mezi časy.

- Výsledek jakékoli aritmetické nebo srovnávací operace provedené na <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> dvou hodnotách data a času, jejichž vlastnosti se rovnají <xref:System.DateTimeKind> nebo na dvou hodnotách data a času s různými <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotami vlastností odráží rozdíl v čase hodin mezi dvěma hodnotami.

- Aritmetické nebo srovnávací operace s místními hodnotami data a času neberou v úvahu, zda je určitá hodnota nejednoznačná nebo neplatná, ani neberou v úvahu vliv pravidel úprav, která vyplývají z přechodu místního časového pásma na letní čas nebo z nich. šetří čas.

- Každá operace, která porovnává nebo vypočítá rozdíl mezi časem UTC a místním časem, zahrnuje časový interval rovnající se posunu místního časového pásma od času UTC ve výsledku.

- Každá operace, která porovnává nebo vypočítá rozdíl mezi neurčenýčas a buď UTC nebo místní čas odráží jednoduchý čas hodin. Rozdíly v časových pásmech nejsou považovány za a výsledek neodráží použití pravidel úpravy časového pásma.

- Každá operace, která porovnává nebo vypočítá rozdíl mezi dvěma neurčenými časy, může zahrnovat neznámý interval, který odráží rozdíl mezi časem ve dvou různých časových pásmech.

Existuje mnoho scénářů, ve kterých rozdíly v časových pásmech nemají vliv na výpočty data a času (pro diskusi o některé z nich, viz [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) nebo ve kterém kontext data data data a času definuje význam porovnání nebo aritmetické operace.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porovnání a aritmetické operace s hodnotami DateTimeOffset

Hodnota <xref:System.DateTimeOffset> zahrnuje nejen datum a čas, ale také posun, který jednoznačně definuje toto datum a čas vzhledem k času UTC. To umožňuje definovat rovnost poněkud odlišně než <xref:System.DateTimeOffset> pro hodnoty. Vzhledem <xref:System.DateTime> k tomu, že hodnoty jsou stejné, pokud mají stejnou hodnotu data a času, hodnoty jsou stejné, <xref:System.DateTimeOffset> pokud oba odkazují na stejný bod v čase. Díky hodnotě <xref:System.DateTimeOffset> přesnější a méně potřebují interpretaci při použití ve srovnání a ve většině aritmetické operace, které určují interval mezi dvěma daty a časy. Následující příklad, který <xref:System.DateTimeOffset> je ekvivalentní předchozí příklad, který porovnával <xref:System.DateTimeOffset> místní a UTC hodnoty, ilustruje tento rozdíl v chování.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

V tomto příkladu <xref:System.DateTimeOffset.CompareTo%2A> metoda označuje, že aktuální místní čas a aktuální čas <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> UTC jsou stejné a <xref:System.TimeSpan.Zero?displayProperty=nameWithType>odčítání hodnot označuje, že rozdíl mezi dvěma časy je .

Hlavní omezení použití <xref:System.DateTimeOffset> hodnot v aritmetické datum <xref:System.DateTimeOffset> a čas je, že i když hodnoty mají určité povědomí o časovém pásmu, nejsou plně vědomi časové pásmo. Přestože <xref:System.DateTimeOffset> posun hodnoty odráží posun časového pásma od času <xref:System.DateTimeOffset> UTC, když je proměnné poprvé přiřazena hodnota, stane se poté odpojenod časového pásma. Vzhledem k tomu, že již není přímo spojena s identifikovatelný čas, sčítání a odčítání data a časové intervaly nebere v úvahu pravidla úprav časového pásma.

Pro ilustraci přechod na letní čas v americkém centrálním standardním časovém pásmu probíhá ve 2:00. 9. března 2008. To znamená, že přidání intervalu dvě a půl hodiny centrálního standardního času 1:30 am března 2008, by měla produkovat datum a čas 5:00 am 9. března 2008. Nicméně, jak ukazuje následující příklad, výsledek přidání je 4:00 AM. 9. března 2008. Všimněte si, že výsledek této operace představuje správný bod v čase, i když to není čas v časovém pásmu, ve kterém máme zájem (to znamená, že nemá očekávané časové pásmo posun).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Aritmetické operace s časy v časových pásmech

Třída <xref:System.TimeZoneInfo> obsahuje řadu metod převodu, které automaticky použijí úpravy při převodu časů z jednoho časového pásma do druhého. Patří mezi ně například:

- Metody <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> a, které převádějí časy mezi libovolnými dvěma časovými pásmy.

- Metody <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> a, které převádějí čas v určitém časovém pásmu na Čas UTC nebo převedou čas UTC na čas v určitém časovém pásmu.

Podrobnosti naleznete v [tématu Převod časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

Třída <xref:System.TimeZoneInfo> neposkytuje žádné metody, které automaticky používají pravidla úprav při provádění aritmetiky data a času. Můžete to však provést převedením času v časovém pásmu na čas UTC, provedením aritmetické operace a následným převodem z času UTC zpět na čas v časovém pásmu. Podrobnosti naleznete [v tématu How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Například následující kód je podobný předchozímu kódu, který přidal dvě a půl hodiny do 2:00. 9. března 2008. Protože však převede centrální standardní čas na Čas UTC před provedením aritmetiky data a času a poté převede výsledek z času UTC zpět na centrální standardní čas, výsledný čas odráží přechod centrálního standardního časového pásma na letní čas. Čas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
