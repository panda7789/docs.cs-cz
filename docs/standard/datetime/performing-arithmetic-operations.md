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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bbd5afb89d2b992e06583c7427c1a25a5b8f273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577542"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Provádění aritmetických operací s daty a časy

I když obě <xref:System.DateTime> a <xref:System.DateTimeOffset> struktury poskytují členy, kteří provádějí aritmetické operace na jejich hodnot, výsledky aritmetické operace se příliš neliší. Toto téma popisuje tyto rozdíly, se vztahují na povědomí o časovém pásmu v datech datum a čas a popisuje, jak provádět plně časové pásmo vědět operace pomocí data a času.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porovnání a aritmetické operace s hodnotami data a času

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Vlastnost umožňuje <xref:System.DateTimeKind> přiřazení na datum a čas k označení, zda představuje místní čas, koordinovaný světový čas (UTC) nebo čas v neurčené časové pásmo hodnoty. Ale tyto informace omezené časové pásmo se ignoruje při porovnávání nebo provádění datum a čas aritmetické na <xref:System.DateTimeKind> hodnoty. Následující příklad, který porovnává aktuální místní čas s aktuální čas UTC, znázorňuje to.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Metoda hlásí, že místní čas je starší než (nebo menší než) na čas UTC a operace odčítání určuje rozdíl mezi místním ČASEM a pro systém v USA Tichomořském časovém pásmu je sedm hodin. Protože tyto dvě hodnoty poskytují různé reprezentace jediný bod v čase, je však vymazat v tomto případě, že tento časový interval je zcela připadající na místní časové pásmo posun od času UTC.

Obecně platí <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nemá vliv na výsledky vrácené <xref:System.DateTime.Kind> porovnání a aritmetické metody (jak značí porovnávání dva identické body v čase), i když může ovlivnit výklad těchto výsledků. Příklad:

* Výsledek jakékoli aritmetické operace provést na dvě hodnoty data a času, jehož <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> obě vlastnosti rovnat <xref:System.DateTimeKind> odráží skutečný časový interval mezi dvěma hodnotami. Podobně při porovnání dvou tyto hodnoty data a času přesně odráží vztah mezi časy.

* Výsledek jakékoli aritmetické operace nebo porovnání provést na dvě hodnoty data a času, jehož <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> rovnat obě vlastnosti <xref:System.DateTimeKind> nebo dvě hodnoty data a času jiné <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnoty vlastností odráží rozdíl v čase mezi tyto dvě hodnoty.

* Aritmetické operace nebo porovnání operací na hodnoty místního data a času nepovažujte zda určitou hodnotu není jednoznačná nebo je neplatný, ani se budou brát v úvahu účinek všechna úpravu pravidla, která způsobit z místního časového pásma přechodu na nebo z letního času Úspora času.

* Všechny operace, který porovnává nebo vypočítá rozdíl mezi místním ČASEM a zahrnuje časový interval, který se rovná místním časovém pásmu posun od času UTC ve výsledku.

* Všechny operace, který porovnává nebo vypočítá rozdíl mezi nespecifikovaný čas a čas UTC nebo místního času bere v. Nejsou považovány za rozdíly časových pásem a výsledek nezohledňuje aplikace pravidla úpravy časového pásma.

* Všechny operace, který porovnává nebo vypočítá rozdíl mezi dvěma neurčené časy může zahrnovat neznámé časový interval, který zobrazuje rozdíl mezi čas ve dvou různých časových pásmech.

Existuje mnoho scénářů, ve kterých časové pásmo rozdíly nemají vliv na výpočty datum a čas (diskuzi o některé z nich, v tématu [volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) nebo ve kterých kontext data a času dat určuje význam porovnávání nebo aritmetických operací.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porovnání a aritmetické operace s hodnotami DateTimeOffset

A <xref:System.DateTimeOffset> hodnota zahrnuje nejen datum a čas, ale také posun, který jednoznačně definuje, že data a času relativně k UTC. Díky tomu je možné definovat rovnost trochu jinak než pro <xref:System.DateTimeOffset> hodnoty. Zatímco <xref:System.DateTime> jsou hodnoty stejné, pokud mají stejné datum a čas hodnotu, <xref:System.DateTimeOffset> jsou hodnoty stejné, pokud obě odkazují na stejný bod v čase. Díky tomu <xref:System.DateTimeOffset> hodnota přesnější a méně náročná interpretace při použití v porovnání a většina aritmetické operace, které určují, interval mezi dvěma data a časy. Následující příklad, který je <xref:System.DateTimeOffset> ekvivalentní předchozí příklad, který porovná místní a UTC <xref:System.DateTimeOffset> hodnoty, ukazuje rozdíl v chování.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

V tomto příkladu <xref:System.DateTimeOffset.CompareTo%2A> metoda označuje, že aktuálním místním časem a aktuální čas UTC jsou stejné a odečtením <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> hodnoty značí, že je rozdíl mezi dvěma časy <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Hlavní omezení použití <xref:System.DateTimeOffset> hodnoty datum a čas aritmetické je, že i když <xref:System.DateTimeOffset> hodnoty mají částečně časové pásmo, nejsou plně časové pásmo vědět. I když <xref:System.DateTimeOffset> hodnoty posunu odráží posun časového pásma od času UTC při <xref:System.DateTimeOffset> hodnotu nejdřív přiřazenou proměnnou, tak se informace o časovém pásmu zruší. Protože je již přímo spojen s identifikací času, sčítání a odečítání datum a čas intervalů nebere v úvahu pravidla úpravy časového pásma.

Pro ilustraci, přechodu na letní čas v USA Střed standardního časového pásma dochází ve 2:00 9. března 2008. To znamená, že přidáním intervalu dva a půl hodiny do centrální běžný čas 1:30: hod 9. března 2008 by měl vytvořit datum a čas 05:00. 9. března 2008. Ale jak ukazuje následující příklad, výsledek přidání je 4:00 9. března 2008. Všimněte si, že tento výsledek této operace představuje konkrétní bod v čase, ačkoli to není čas v časovém pásmu, který jsme zajímá (to znamená, nemá očekávaný časové pásmo posun).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Aritmetické operace s časy v časových pásmech

<xref:System.TimeZoneInfo> Třída obsahuje několik metod převodu, které automaticky aplikují úpravy při převodu časů z jednoho časového pásma na jiný. Patří mezi ně například:

* <xref:System.TimeZoneInfo.ConvertTime%2A> a <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> metody, které převádějí časy mezi každými dvěma časovými pásmy.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> a <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody, které převést čas v určitém časovém pásmu UTC, nebo převést čas v určitém časovém pásmu UTC.

Podrobnosti najdete v tématu [převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Třída neposkytuje žádné metody, které automaticky používají pravidla pro úpravy při provádění datum a čas aritmetické. Můžete to však provést převod času v časovém pásmu UTC, provádění aritmetické operace a pak převodu od času UTC zpět na čas v časovém pásmu. Podrobnosti najdete v tématu [postupy: používání časových pásem datum a čas aritmetické](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Například následující kód je podobná předchozí kód, který přidá dva a půl hodiny do 2:00:00 9. března 2008. Ale protože převede centrální běžný čas na čas UTC, než provede datum a čas aritmetické a následně převádí výsledek od času UTC zpět na střed (běžný čas), výsledný čas zohledňuje střed standardního časového pásma přechodu na letní čas čas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: používání časových pásem datum a čas aritmetické](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
