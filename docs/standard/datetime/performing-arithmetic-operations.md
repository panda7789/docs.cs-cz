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
ms.openlocfilehash: c2a50823b812541786cf1bebfd6b1262ce2e9314
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46482089"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Provádění aritmetických operací s daty a časy

I když obě <xref:System.DateTime> a <xref:System.DateTimeOffset> struktury poskytovaly členy, které provádějí aritmetické operace na hodnotách, se velmi liší výsledky aritmetické operace. Toto téma popisuje tyto rozdíly, se vztahují na časové pásmo sledování data a času a popisuje, jak k provádění plně časové pásmo vědět operací pomocí data a času.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porovnání a aritmetické operace s hodnotami data a času

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Vlastnost umožňuje <xref:System.DateTimeKind> hodnota, která má být přiřazena k datu a času, který označuje, zda představuje místní čas, koordinovaný univerzální čas (UTC) nebo čas v nespecifikovaného časového pásma. Ale tyto informace omezené časové pásmo se ignoruje při porovnávání nebo provádění v aritmetice kalendářních a časových <xref:System.DateTimeKind> hodnoty. Dokládá následující příklad, který porovná aktuální místní čas s aktuálním časem UTC.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Metoda hlásí, že je starší než místní čas (nebo menší než), který označuje čas UTC a operace odčítání rozdíl mezi UTC a lokálního časového systému v USA Tichomořském časovém pásmu je sedm hodin. Ale vzhledem k tomu, že tyto dvě hodnoty poskytují různé reprezentace jediný bod v čase, je jasné v tomto případě, že tento časový interval je zcela odvoditelný posun místního časového pásma od času UTC.

Obecně platí <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> vlastnost nemá vliv na výsledky vrácené <xref:System.DateTime.Kind> porovnání a aritmetické operace metody (jak určuje porovnání dvou identických bodů v čase), i když může ovlivnit interpretace výsledků. Příklad:

* Výsledek všechny aritmetické operace provedené na dvě hodnoty datum a čas, jehož <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> obě vlastnosti rovnat <xref:System.DateTimeKind> odráží skutečný časový interval mezi dvěma hodnotami. Obdobně porovnání dvou tyto hodnoty data a času přesně odráží vztah mezi časy.

* Výsledek všechny aritmetické operace nebo porovnání provedené na dvě hodnoty datum a čas, jehož <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> obě vlastnosti rovnat <xref:System.DateTimeKind> nebo na dvě hodnoty data a času s různými <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hodnoty vlastností odráží rozdíl v čase mezi dvěma hodnotami.

* Aritmetické operace nebo jejich porovnávání operací na hodnotách místní data a času Neberte v úvahu, jestli konkrétní hodnoty je nejednoznačný nebo není platný, ani přebírají účet efekt pravidla jakékoli úpravy, které vyplývají z místního časového pásma přechod do nebo z letního času Úspora času.

* Všechny operace, která porovnává nebo vypočítá rozdíl mezi místním časem a UTC zahrnuje časový interval, který se rovná posun místního časového pásma od UTC ve výsledku.

* Všechny operace, která porovnává nebo vypočítá rozdíl mezi nespecifikovaný čas a čas UTC nebo místního času odráží jednoduché čas. Rozdíly v časových pásmech nejsou považovány za a výsledek neodráží aplikace pravidla úpravy časového pásma.

* Všechny operace, která porovnává nebo vypočítá rozdíl mezi dvěma tento parametr zadán časy mohou zahrnovat neznámý interval, který zobrazuje rozdíl mezi časem v různých časových pásmech.

Existuje mnoho scénářů, ve které časové pásmo rozdíly nemají vliv na data a času výpočty (diskuzi o některé z nich, naleznete v tématu [volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) nebo ve kterém kontextu data a času definuje datový význam porovnání nebo aritmetických operací.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porovnání a aritmetické operace s hodnotami DateTimeOffset

A <xref:System.DateTimeOffset> hodnota obsahuje nejen data a času, ale také posunu, který jednoznačně určuje tento data a času relativně k času UTC. To umožňuje definovat rovnost trochu jinak než pro <xref:System.DateTimeOffset> hodnoty. Vzhledem k tomu <xref:System.DateTime> jsou hodnoty stejné, pokud mají stejné datum a čas, <xref:System.DateTimeOffset> jsou hodnoty stejné, pokud oba odkazují na stejný bod v čase. Díky tomu <xref:System.DateTimeOffset> hodnotu přesné a méně náročná na vyhodnocení při použití v porovnávání a ve většině aritmetické operace, které určují interval mezi dvěma data a časy. V následujícím příkladu, který je <xref:System.DateTimeOffset> ekvivalentní k předchozímu příkladu, který porovnání místní a standardem UTC <xref:System.DateTimeOffset> hodnoty, ukazuje rozdíl v chování.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

V tomto příkladu <xref:System.DateTimeOffset.CompareTo%2A> metoda označuje, že aktuálním místním časem a do aktuálního času UTC jsou stejné a odečtení <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> hodnoty označuje, že je rozdíl mezi dvěma časy <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Hlavní omezení použití <xref:System.DateTimeOffset> hodnoty v aritmetice kalendářních a časových je, že i když <xref:System.DateTimeOffset> hodnoty mají některé časové pásmo, nejsou plně časové pásmo vědět. I když <xref:System.DateTimeOffset> hodnoty posunu zahrnuje posun časového pásma od UTC při <xref:System.DateTimeOffset> proměnná je první přiřazená hodnota, tak se stane po tomto datu informace o časovém pásmu. Protože už nejsou přímo spojené s identifikací času, sčítání a odčítání datum a čas intervalů, které nebere v úvahu pravidla úpravy časového pásma.

Pro ilustraci, přechodu na letní čas v USA. Vyvolá se centrální standardního časového pásma ve 2:00:00 9. března, 2008. To znamená, že přidáte dva a půl hodiny interval centrální běžný čas 1:30 hod 9. března, 2008 mohou být vráceny datum a čas 5:00:00. 9. března, 2008. Jak ukazuje následující příklad, výsledek součtu je však 4:00:00. 9. března, 2008. Všimněte si, že tento výsledek této operace představují správného bodu v čase, i když není čas v časovém pásmu, které nás zajímá (tedy nemá očekávaný časové pásmo posun).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Aritmetické operace s časem v časových pásmech

<xref:System.TimeZoneInfo> Třída zahrnuje celou řadu metod pro převod, které se automaticky aplikují úpravy při převést časy z jedné časové pásmo na jiný. Patří mezi ně například:

* <xref:System.TimeZoneInfo.ConvertTime%2A> a <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> metody, které převést časy mezi jakékoli dvě časových pásem.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> a <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody, které Převeďte čas v určitém časovém pásmu na UTC, nebo převést na čas v určitém časovém pásmu UTC.

Podrobnosti najdete v tématu [převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Třída neposkytuje žádné metody, které automaticky používají pravidla pro úpravy při provádění aritmetika data a času. Můžete to však provést převod čas v časovém pásmu UTC, provádí aritmetické operace a pak převod ze standardu UTC zpět na čas v časovém pásmu. Podrobnosti najdete v tématu [postupy: používání časových pásem v aritmetice kalendářních a časových](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Například následující kód je podobný jako předchozí kód, který přidá dvě a půl hodiny 2:00:00 9. března, 2008. Ale protože centrální běžný čas převede na UTC předtím, než provede aritmetika data a času a poté převádí výsledek od času UTC zpět na střed (běžný čas), výsledný čas odráží zóny centrální běžný čas přechodu na letní čas čas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Viz také:

* [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
* [Postupy: Používání časových pásem v aritmetice kalendářních a časových údajů](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
