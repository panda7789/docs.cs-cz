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
ms.openlocfilehash: 2e668cf3f909ed4b89f05ca63dfe69051c1d9066
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122268"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Provádění aritmetických operací s daty a časy

I když <xref:System.DateTime> i <xref:System.DateTimeOffset> struktury poskytují členy, kteří provádějí aritmetické operace s jejich hodnotami, výsledky aritmetických operací se velmi liší. V tomto tématu se tyto rozdíly prozkoumají, pokud jde o stupně povědomí časových pásem v datech data a času a popisuje, jak provádět operace s neomezenou časovou zónou pomocí dat data a času.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porovnávání a aritmetické operace s hodnotami DateTime

Vlastnost <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> umožňuje přiřadit hodnotu <xref:System.DateTimeKind> data a času k označení, zda představuje místní čas, koordinovaný světový čas (UTC) nebo čas v neurčeném časovém pásmu. Tyto informace o omezeném časovém pásmu se ale ignorují při porovnávání nebo provádění aritmetických operací s daty a časy <xref:System.DateTimeKind> hodnot. Následující příklad, který porovnává aktuální místní čas s aktuálním časem UTC, znázorňuje toto.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

Metoda <xref:System.DateTime.CompareTo%28System.DateTime%29> hlásí, že místní čas je dřívější než (nebo je menší než) čas UTC a operace odčítání označuje, že rozdíl mezi časem UTC a místním časem pro systém v oblasti USA (běžný čas) je sedm hodin. Vzhledem k tomu, že tyto dvě hodnoty poskytují různé reprezentace jednoho bodu v čase, je v tomto případě jasné, že tento časový interval je zcela přizpůsoben posunu místního časového pásma od času UTC.

Obecně platí, že vlastnost <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> nemá vliv na výsledky vrácené <xref:System.DateTime.Kind> porovnání a aritmetické metody (jako porovnání dvou identických bodů v čase), přestože může ovlivnit výklad těchto výsledků. Příklad:

- Výsledek jakékoli aritmetické operace provedené na dvou hodnotách data a času, jejichž <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti se shodují <xref:System.DateTimeKind> odráží skutečný časový interval mezi dvěma hodnotami. Podobně porovnání dvou těchto hodnot data a času přesně odráží vztah mezi časy.

- Výsledek jakékoli aritmetické operace nebo operace porovnání provedené na dvou hodnotách data a času, jejichž <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnosti jsou stejné <xref:System.DateTimeKind> nebo na dvou hodnotách data a času s různými hodnotami vlastností <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>, odráží rozdíl v časovém intervalu mezi dvěma hodnota.

- Aritmetické operace nebo operace porovnání s místními hodnotami data a času neuvažují o tom, zda je určitá hodnota nejednoznačná nebo neplatná, ani nebere v úvahu účinek všech pravidel úprav, která vznikne přechodum z místního časového pásma do nebo z oblasti letního času. šetří se čas.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi časem UTC a místním časem, obsahuje časový interval, který se rovná posunu místního časového pásma od času UTC ve výsledku.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi nespecifikovaným časem a buď časem UTC, nebo místním časem, odráží jednoduchou časovou prodlevu. Rozdíly v časovém pásmu se nepovažují a výsledek neodráží použití pravidel úprav časových pásem.

- Jakákoli operace, která porovnává nebo vypočítá rozdíl mezi dvěma nespecifikovanými časy, může zahrnovat neznámý interval, který odráží rozdíl mezi časem ve dvou různých časových pásmech.

Existuje mnoho scénářů, ve kterých rozdíly v časovém pásmu neovlivňují výpočty data a času (pro diskuzi některé z těchto možností, viz [Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) nebo v němž kontext dat data a času. definuje význam porovnání nebo aritmetické operace.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porovnávání a aritmetické operace s hodnotami DateTimeOffset

Hodnota <xref:System.DateTimeOffset> zahrnuje nejen datum a čas, ale také posun, který jednoznačně definuje toto datum a čas relativní ke standardu UTC. Díky tomu je možné definovat rovnost trochu jinak než u <xref:System.DateTimeOffset>ch hodnot. Vzhledem k tomu, že <xref:System.DateTime> hodnoty jsou stejné, pokud mají stejnou hodnotu data a času, <xref:System.DateTimeOffset> hodnoty jsou stejné, pokud obě odkazují na stejný bod v čase. Díky tomu je hodnota <xref:System.DateTimeOffset> přesnější a méně pro potřebu výkladu při použití v porovnání a ve většině aritmetických operací, které určují interval mezi dvěma daty a časy. Následující příklad, který je <xref:System.DateTimeOffset> ekvivalentem k předchozímu příkladu, který porovnává místní a UTC <xref:System.DateTimeOffset> hodnoty, ukazuje tento rozdíl v chování.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

V tomto příkladu metoda <xref:System.DateTimeOffset.CompareTo%2A> označuje, že aktuální místní čas a aktuální čas UTC jsou stejné a odečtení <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> hodnot znamená, že rozdíl mezi dvěma časy je <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Hlavní omezení použití <xref:System.DateTimeOffset> hodnot v aritmetickém datu a čase je, že i když <xref:System.DateTimeOffset> hodnoty mají nějaké povědomí o časovém pásmu, neexistují na nich plně nevědomá časová pásma. I když posun hodnoty <xref:System.DateTimeOffset> odráží posun časového pásma od času UTC, kdy se k proměnné <xref:System.DateTimeOffset> poprvé přiřadí hodnota, dojde k jejímu odstoupení od časového pásma. Vzhledem k tomu, že již není přímo spojen s identifikovatelným časem, sčítání a odčítání časových intervalů nebere v úvahu pravidla úpravy časového pásma.

Pro ilustraci se přechod na letní čas v centrálním časovém pásmu USA nachází v 2:00. ráno. 9\. března 2008. To znamená, že přidání dvou a půl hodinového intervalu do centrálního standardního času 1:30 dop. 9\. března 2008 by měl vytvořit datum a čas 5:00 dop. 9\. března 2008. Jak ukazuje následující příklad, výsledek přidání je 4:00 dop. 9\. března 2008. Všimněte si, že tento výsledek této operace představuje správný bod v čase, i když se nejedná o čas v časovém pásmu, ve kterém se zajímá (to znamená, že nemá očekávané posunutí časového pásma).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Aritmetické operace s časy v časových pásmech

Třída <xref:System.TimeZoneInfo> zahrnuje řadu metod převodu, které automaticky aplikují úpravy při převodu časů z jednoho časového pásma na jiný. Patří mezi ně například:

- Metody <xref:System.TimeZoneInfo.ConvertTime%2A> a <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, které převádějí časy mezi dvěma časovými pásmy.

- Metody <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> a <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, které převádějí čas v konkrétním časovém pásmu na čas UTC nebo převádějí čas UTC na čas v konkrétním časovém pásmu.

Podrobnosti najdete v tématu [Převod časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

Třída <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> neposkytuje žádné metody, které automaticky použijí pravidla úprav při provádění aritmetických operací s daty a časem. To však lze provést převedením času v časovém pásmu na čas UTC, provedením aritmetické operace a následným převodem z formátu UTC zpět na čas v časovém pásmu. Podrobnosti naleznete v tématu [How to: use časová pásma v aritmetickém datu a čase](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Například následující kód je podobný předchozímu kódu, který přidal dvě až půl hodiny do 2:00 dop. 9\. března 2008. Vzhledem k tomu, že převede centrální standardní čas na čas UTC před tím, než provede aritmetické operace data a času, a poté převede výsledek z času UTC zpět na střední čas, výsledný čas odráží přechod centrálního standardního časového pásma na letní čas. interval.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
