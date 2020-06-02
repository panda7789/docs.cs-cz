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
ms.openlocfilehash: c212397f99bd09195f298d7d704c879705b14f02
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281541"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Provádění aritmetických operací s daty a časy

I když <xref:System.DateTime> <xref:System.DateTimeOffset> struktury i poskytují členy, kteří provádějí aritmetické operace s jejich hodnotami, výsledky aritmetických operací se velmi liší. V tomto tématu se tyto rozdíly prozkoumají, pokud jde o stupně povědomí časových pásem v datech data a času a popisuje, jak provádět operace s neomezenou časovou zónou pomocí dat data a času.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porovnávání a aritmetické operace s hodnotami DateTime

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>Vlastnost umožňuje <xref:System.DateTimeKind> přiřadit hodnotu k datu a času k označení, zda představuje místní čas, koordinovaný světový čas (UTC) nebo čas v neurčeném časovém pásmu. Tyto informace o omezeném časovém pásmu se ale ignorují při porovnávání nebo provádění aritmetických operací s hodnotami data a času <xref:System.DateTimeKind> . Následující příklad, který porovnává aktuální místní čas s aktuálním časem UTC, znázorňuje toto.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29>Metoda hlásí, že místní čas je dřívější než (nebo je menší než) čas UTC, a operace odčítání označuje, že rozdíl mezi časem UTC a místním časem pro systém v americké oblasti v oblasti USA (běžný čas) je sedm hodin. Vzhledem k tomu, že tyto dvě hodnoty poskytují různé reprezentace jednoho bodu v čase, je v tomto případě jasné, že časový interval je zcela přizpůsoben posunu místního časového pásma od času UTC.

Obecně platí, že <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nemá vliv na výsledky vrácené <xref:System.DateTime.Kind> porovnáním a aritmetickými metodami (jako porovnání dvou identických bodů v čase), přestože může ovlivnit výklad těchto výsledků. Například:

- Výsledek jakékoli aritmetické operace provedené na dvou hodnotách data a času, jejichž <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti oba odpovídají <xref:System.DateTimeKind> , odráží skutečný časový interval mezi dvěma hodnotami. Podobně porovnání dvou těchto hodnot data a času přesně odráží vztah mezi časy.

- Výsledek jakékoli aritmetické operace nebo operace porovnání provedené na dvou hodnotách data a času, jejichž <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti jsou stejné <xref:System.DateTimeKind> nebo u dvou hodnot data a času s různými <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnotami vlastností, odráží rozdíl v časovém intervalu mezi dvěma hodnotami.

- Aritmetické operace nebo operace porovnání s místními hodnotami data a času neberou v úvahu, zda je určitá hodnota nejednoznačná nebo neplatná, ani nebere v úvahu účinek všech pravidel úprav, která jsou výsledkem přechodu z místního časového pásma do nebo z letního času.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi časem UTC a místním časem, obsahuje časový interval, který se rovná posunu místního časového pásma od času UTC ve výsledku.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi nespecifikovaným časem a buď časem UTC, nebo místním časem, odráží jednoduchou časovou prodlevu. Rozdíly v časovém pásmu se nepovažují a výsledek neodráží použití pravidel úprav časových pásem.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi dvěma nespecifikovanými časy, může zahrnovat neznámý interval, který odráží rozdíl mezi časem ve dvou různých časových pásmech.

Existuje mnoho scénářů, ve kterých rozdíly v časovém pásmu neovlivňují výpočty data a času (pro diskuzi některé z těchto možností, viz [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](choosing-between-datetime.md)) nebo v němž kontext dat data a času definuje význam porovnání nebo aritmetické operace.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porovnávání a aritmetické operace s hodnotami DateTimeOffset

<xref:System.DateTimeOffset>Hodnota zahrnuje nejen datum a čas, ale také posun, který jednoznačně definuje toto datum a čas relativní ke standardu UTC. Díky tomu je možné definovat rovnost trochu jinak než u <xref:System.DateTimeOffset> hodnot. Vzhledem k tomu <xref:System.DateTime> , že hodnoty jsou stejné, pokud mají stejnou hodnotu data a času, <xref:System.DateTimeOffset> hodnoty jsou stejné, pokud obě odkazují na stejný bod v čase. Díky tomu je <xref:System.DateTimeOffset> hodnota přesnější a méně v potřebu výkladu při použití v porovnání a ve většině aritmetických operací, které určují interval mezi dvěma daty a časy. Následující příklad, který je <xref:System.DateTimeOffset> ekvivalentem předchozího příkladu, který porovnává místní a UTC <xref:System.DateTimeOffset> hodnoty, ilustruje tento rozdíl v chování.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

V tomto příkladu <xref:System.DateTimeOffset.CompareTo%2A> Metoda označuje, že aktuální místní čas a aktuální čas UTC jsou stejné a odečtení <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> hodnot značí, že rozdíl mezi dvěma časy je <xref:System.TimeSpan.Zero?displayProperty=nameWithType> .

Hlavní omezení použití <xref:System.DateTimeOffset> hodnot v aritmetických operacích data a času je tím, že i když <xref:System.DateTimeOffset> hodnoty mají nějaké informace o časovém pásmu, nepodporují neomezenou časovou zónu. I když <xref:System.DateTimeOffset> posun hodnoty odráží posun časového pásma od času UTC <xref:System.DateTimeOffset> , když je proměnné nejprve přiřazena hodnota, dojde k jejímu odstoupení od časového pásma. Vzhledem k tomu, že již není přímo spojen s identifikovatelným časem, sčítání a odčítání časových intervalů nebere v úvahu pravidla úpravy časového pásma.

Pro ilustraci se přechod na letní čas v centrálním časovém pásmu USA nachází v 2:00. ráno. 9. března 2008. To znamená, že přidání dvou a půl hodinového intervalu do centrálního standardního času 1:30 dop. 9. března 2008 by měl vytvořit datum a čas 5:00 dop. 9. března 2008. Jak ukazuje následující příklad, výsledek přidání je 4:00 dop. 9. března 2008. Všimněte si, že výsledek této operace představuje správný bod v čase, přestože se nejedná o čas v časovém pásmu, ve kterém se zajímá (to znamená, že nemá očekávané posunutí časového pásma).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Aritmetické operace s časy v časových pásmech

<xref:System.TimeZoneInfo>Třída obsahuje počet metod převodu, které automaticky aplikují úpravy při převodu časů z jednoho časového pásma na jiný. Patří mezi ně například:

- <xref:System.TimeZoneInfo.ConvertTime%2A>Metody a <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> , které převádějí časy mezi dvěma časovými pásmy.

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>Metody a <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> , které převádějí čas v konkrétním časovém pásmu na čas UTC nebo převádějí čas UTC na čas v konkrétním časovém pásmu.

Podrobnosti najdete v tématu [Převod časů mezi časovými pásmy](converting-between-time-zones.md).

<xref:System.TimeZoneInfo>Třída neposkytuje žádné metody, které automaticky použijí pravidla úprav při provádění aritmetických operací s daty a časem. To však lze provést převedením času v časovém pásmu na čas UTC, provedením aritmetické operace a následným převodem z formátu UTC zpět na čas v časovém pásmu. Podrobnosti naleznete v tématu [How to: use časová pásma v aritmetickém datu a čase](use-time-zones-in-arithmetic.md).

Například následující kód je podobný předchozímu kódu, který přidal dvě až půl hodiny do 2:00 dop. 9. března 2008. Vzhledem k tomu, že převede centrální standardní čas na čas UTC před tím, než provede aritmetické operace s datem a časem, a poté převede výsledek z času UTC zpět na střední čas (běžný čas), výsledný čas odráží přechod centrálního standardního časového pásma na letní čas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů](use-time-zones-in-arithmetic.md)
