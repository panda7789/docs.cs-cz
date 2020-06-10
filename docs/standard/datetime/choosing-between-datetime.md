---
title: Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo
description: Naučte se vybírat mezi typy DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo, které reprezentují informace o datu a čase v .NET.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
ms.openlocfilehash: 0b89d0fd36af00796105af50f51803c90cce2605
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662807"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo

Aplikace .NET, které používají informace o datu a čase, jsou velmi rozdílné a můžou tyto informace použít několika způsoby. Mezi běžně používané informace o datu a času patří následující:

- Aby odrážela pouze datum, takže časové údaje nejsou důležité.

- Odrážející jenom čas, takže informace o datu nejsou důležité.

- Aby odrážela abstraktní datum a čas, který není vázán na určitý čas a místo (například většina obchodů v mezinárodním řetězci otevřeném v pracovních dnech v 9:00 ráno).

- Chcete-li načíst informace o datu a čase ze zdrojů mimo rozhraní .NET, obvykle v případě, kdy jsou informace o datu a čase uloženy v jednoduchém datovém typu.

- Pro jednoznačnou a jednoznačně identifikují jediný bod v čase. Některé aplikace vyžadují, aby bylo datum a čas dvojznačné jenom v hostitelském systému. jiné vyžadují, aby byly v rámci systémů jednoznačně deserializovatelné a používané v jiném systému kdekoli na světě, ale data serializovaná v jednom systému.

- Chcete-li zachovat více souvisejících časů (například místní čas žadatele a čas serveru pro webový požadavek).

- K provedení aritmetického zpracování data a času, případně s výsledkem jednoznačně a jednoznačně identifikuje jediný bod v čase.

Rozhraní .NET zahrnuje <xref:System.DateTime> <xref:System.DateTimeOffset> typy,, <xref:System.TimeSpan> a <xref:System.TimeZoneInfo> , které lze použít k sestavování aplikací pracujících s daty a časy.

> [!NOTE]
> Toto téma se nezabývá vzhledem k tomu, <xref:System.TimeZone> že jeho funkce jsou skoro zcela začleněné do <xref:System.TimeZoneInfo> třídy. Kdykoli je to možné, použijte <xref:System.TimeZoneInfo> místo třídy třídu <xref:System.TimeZone> .

## <a name="the-datetime-structure"></a>Struktura DateTime

<xref:System.DateTime>Hodnota definuje konkrétní datum a čas. Obsahuje <xref:System.DateTime.Kind%2A> vlastnost, která poskytuje omezené informace o časovém pásmu, do kterého patří datum a čas. <xref:System.DateTimeKind>Hodnota vrácená <xref:System.DateTime.Kind%2A> vlastností označuje, zda <xref:System.DateTime> hodnota představuje místní čas ( <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ), KOORDINOVANÝ světový čas (UTC) ( <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ) nebo nespecifikovaný čas ( <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> ).

<xref:System.DateTime>Struktura je vhodná pro aplikace, které mají následující:

- Pracují pouze s kalendářními daty.

- Pracujte pouze s časy.

- Pracujte s abstraktními daty a časy.

- Pracujte s daty a časy, pro které chybí informace o časovém pásmu.

- Pracovat pouze s časovými údaji a časem UTC.

- Načte informace o datu a čase ze zdrojů mimo rozhraní .NET, jako jsou databáze SQL. Obvykle tyto zdroje ukládají informace o datu a čase v jednoduchém formátu, který je kompatibilní se <xref:System.DateTime> strukturou.

- Provádění aritmetických operací s datem a časem, ale s obecnými výsledky. Například v operaci sčítání, která přidá šest měsíců do konkrétní datum a čas, často není důležité, aby byl výsledek upraven pro letní čas.

Pokud konkrétní <xref:System.DateTime> hodnota představuje UTC, tato hodnota data a času je v přenositelnosti často nejednoznačná nebo omezená. Pokud například <xref:System.DateTime> hodnota představuje místní čas, je přenosné v rámci tohoto místního časového pásma (tj. Pokud je hodnota deserializována v jiném systému ve stejném časovém pásmu, tato hodnota stále jednoznačně identifikuje jediný bod v čase). Mimo místní časové pásmo <xref:System.DateTime> může mít tato hodnota více výkladů. Pokud <xref:System.DateTime.Kind%2A> je vlastnost hodnoty <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , je ještě méně přenosná: je nyní nejednoznačná v rámci stejného časového pásma a případně i ve stejném systému, ve kterém byla poprvé serializována. Pouze pokud <xref:System.DateTime> hodnota představuje UTC, tato hodnota jednoznačně identifikuje jediný bod v čase bez ohledu na systém nebo časové pásmo, ve kterém je hodnota použita.

> [!IMPORTANT]
> Při ukládání nebo sdílení <xref:System.DateTime> dat by se měla použít UTC a <xref:System.DateTime> <xref:System.DateTime.Kind%2A> vlastnost hodnoty by měla být nastavená na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

<xref:System.DateTimeOffset>Struktura představuje hodnotu data a času spolu s posunem, který označuje, jak velká hodnota se liší od času UTC. Proto hodnota vždy jednoznačně identifikuje jediný bod v čase.

<xref:System.DateTimeOffset>Typ zahrnuje všechny funkce <xref:System.DateTime> typu společně s vědomím časového pásma. To je vhodné pro aplikace, které provedly následující akce:

- Jedinečně a jednoznačně identifikují jediný bod v čase. <xref:System.DateTimeOffset>Typ lze použít k jednoznačnému definování významu "nyní", k protokolování časů transakcí, k protokolování časů události systému nebo aplikace a k záznamu časů vytváření a úprav souborů.

- Proveďte obecné aritmetické operace data a času.

- Zachovejte více souvisejících časů, pokud jsou tyto časy uloženy jako dvě samostatné hodnoty nebo jako dva členy struktury.

> [!NOTE]
> Tato použití pro <xref:System.DateTimeOffset> hodnoty jsou mnohem častější než u <xref:System.DateTime> hodnot. V důsledku toho <xref:System.DateTimeOffset> by se měl považovat za výchozí typ data a času pro vývoj aplikací.

<xref:System.DateTimeOffset>Hodnota není svázána s konkrétním časovým pásmem, ale může pocházet z celé řady časových pásem. Pro ilustraci tohoto příkladu obsahuje následující příklad časová pásma, do kterých <xref:System.DateTimeOffset> může patřit určitý počet hodnot (včetně místního tichomořského času).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Výstup ukazuje, že každá hodnota data a času v tomto příkladu může patřit alespoň do tří různých časových pásem. <xref:System.DateTimeOffset>Hodnota 6/10/2007 ukazuje, že pokud hodnota data a času představuje letní čas, jeho posun od času UTC ještě nutně neodpovídá základnímu posunu UTC počátečního časového pásma nebo k posunu od času UTC, který se nachází v jeho zobrazovaném názvu. To znamená, že vzhledem k tomu, že jedna <xref:System.DateTimeOffset> hodnota není pevně spojená s časovým pásmem, nemůže odrážet přechod časového pásma do a z letního času. To může být obzvláště problematické, pokud se k manipulaci s hodnotou používá aritmetickí data a času <xref:System.DateTimeOffset> . Diskuzi o tom, jak provádět aritmetické operace s daty a časy způsobem, který bere v úvahu pravidla úpravy časového pásma, najdete v tématu [provádění aritmetických operací s daty a časy](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>Struktura TimeSpan

<xref:System.TimeSpan>Struktura představuje časový interval. Mezi dvě Typická použití patří:

- Odráží časový interval mezi dvěma hodnotami data a času. Například odečtením jedné <xref:System.DateTime> hodnoty z jiné vrátí <xref:System.TimeSpan> hodnotu.

- Měření uplynulého času. Například <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> vlastnost vrací <xref:System.TimeSpan> hodnotu, která odráží časový interval, který uplynul od volání jedné z <xref:System.Diagnostics.Stopwatch> metod, která začíná měřit uplynulý čas.

<xref:System.TimeSpan>Hodnotu lze použít také jako náhradu <xref:System.DateTime> hodnoty, pokud tato hodnota odráží čas bez odkazů na konkrétní den. Toto použití je podobné <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> vlastnostem a, která vrací <xref:System.TimeSpan> hodnotu, která představuje čas bez odkazování na datum. <xref:System.TimeSpan>Struktura může například sloužit ke znázornění každodenního otevření nebo ukončení obchodu nebo může být použita k vyjádření času, kdy dojde k jakékoli běžné události.

Následující příklad definuje `StoreInfo` strukturu, která zahrnuje <xref:System.TimeSpan> objekty pro ukládání počátečních a koncových časů a také <xref:System.TimeZoneInfo> objekt, který představuje časové pásmo obchodu. Struktura také obsahuje dvě metody `IsOpenNow` a `IsOpenAt` , která označuje, zda je úložiště otevřeno v čase určeném uživatelem, který se předpokládá v místním časovém pásmu.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo`Strukturu pak může používat klientský kód podobný následujícímu.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Třída TimeZoneInfo

<xref:System.TimeZoneInfo>Třída představuje jakékoli časové pásmo země a umožňuje převod jakéhokoli data a času v jednom časovém pásmu na jeho ekvivalent v jiném časovém pásmu. <xref:System.TimeZoneInfo>Třída umožňuje pracovat s daty a časy, aby každá hodnota data a času jednoznačně identifikovala jediný bod v čase. <xref:System.TimeZoneInfo>Třída je také rozšiřitelná. I když závisí na informacích o časovém pásmu, které jsou k dispozici pro systémy Windows a definované v registru, podporuje vytváření vlastních časových pásem. Podporuje také serializaci a deserializaci informací o časovém pásmu.

V některých případech <xref:System.TimeZoneInfo> může použití úplné výhody třídy vyžadovat další vývojovou práci. Pokud hodnoty data a času nejsou pevně spojeny s časovými pásmy, ke kterým patří, je vyžadována další práce. Pokud vaše aplikace neposkytuje nějaký mechanismus pro propojení data a času s přidruženým časovým pásmem, je možné, že konkrétní hodnota data a času se stane nepřidruženým k časovému pásmu. Jednou z metod propojení těchto informací je definování třídy nebo struktury, která obsahuje hodnotu data a času a souvisejícího objektu časového pásma.

Využití výhod časových pásem v rozhraní .NET je možné pouze v případě, že časové pásmo, do kterého patří hodnota data a času, je známo při vytváření instance objektu data a času. To se často nejedná o případ, zejména v webových nebo síťových aplikacích.

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
