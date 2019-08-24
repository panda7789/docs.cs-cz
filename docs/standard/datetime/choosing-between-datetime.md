---
title: Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d2ae7430c10254274eed6fb8a602aa8bc11bffb
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988493"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo

Aplikace .NET, které používají informace o datu a čase, jsou velmi rozdílné a můžou tyto informace použít několika způsoby. Mezi běžně používané informace o datu a času patří následující:

* Aby odrážela pouze datum, takže časové údaje nejsou důležité.

* Odrážející jenom čas, takže informace o datu nejsou důležité.

* Aby odrážela abstraktní datum a čas, který není vázán na určitý čas a místo (například většina obchodů v mezinárodním řetězci otevřeném v pracovních dnech v 9:00 ráno).

* Chcete-li načíst informace o datu a čase ze zdrojů mimo rozhraní .NET, obvykle v případě, kdy jsou informace o datu a čase uloženy v jednoduchém datovém typu.

* Pro jednoznačnou a jednoznačně identifikují jediný bod v čase. Některé aplikace vyžadují, aby bylo datum a čas dvojznačné jenom v hostitelském systému. jiné vyžadují, aby byly v rámci systémů jednoznačně deserializovatelné a používané v jiném systému kdekoli na světě, ale data serializovaná v jednom systému.

* Chcete-li zachovat více souvisejících časů (například místní čas žadatele a čas serveru pro webový požadavek).

* K provedení aritmetického zpracování data a času, případně s výsledkem jednoznačně a jednoznačně identifikuje jediný bod v čase.

Rozhraní .NET zahrnuje <xref:System.DateTime>typy <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, a <xref:System.TimeZoneInfo> , které lze použít k sestavování aplikací pracujících s daty a časy.

> [!NOTE]
> Toto téma se nezabývá <xref:System.TimeZone> vzhledem k tomu, že jeho funkce jsou skoro zcela začleněné <xref:System.TimeZoneInfo> do třídy. Kdykoli je to možné, <xref:System.TimeZoneInfo> použijte místo <xref:System.TimeZone> třídy třídu.

## <a name="the-datetime-structure"></a>Struktura DateTime

<xref:System.DateTime> Hodnota definuje konkrétní datum a čas. Obsahuje <xref:System.DateTime.Kind%2A> vlastnost, která poskytuje omezené informace o časovém pásmu, do kterého patří datum a čas. <xref:System.DateTime> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType><xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>Hodnota vrácená <xref:System.DateTime.Kind%2A> vlastností označuje, zda hodnota představuje místní čas (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), koordinovaný světový čas (UTC) () nebo nespecifikovaný čas (). <xref:System.DateTimeKind>

<xref:System.DateTime> Struktura je vhodná pro aplikace, které mají následující:

* Pracují pouze s kalendářními daty.

* Pracujte pouze s časy.

* Pracujte s abstraktními daty a časy.

* Pracujte s daty a časy, pro které chybí informace o časovém pásmu.

* Pracovat pouze s časovými údaji a časem UTC.

* Načte informace o datu a čase ze zdrojů mimo rozhraní .NET, jako jsou databáze SQL. Obvykle tyto zdroje ukládají informace o datu a čase v jednoduchém formátu, který je kompatibilní se <xref:System.DateTime> strukturou.

* Provádění aritmetických operací s datem a časem, ale s obecnými výsledky. Například v operaci sčítání, která přidá šest měsíců do konkrétní datum a čas, často není důležité, aby byl výsledek upraven pro letní čas.

Pokud konkrétní <xref:System.DateTime> hodnota představuje UTC, tato hodnota data a času je v přenositelnosti často nejednoznačná nebo omezená. Pokud <xref:System.DateTime> například hodnota představuje místní čas, je přenosné v rámci tohoto místního časového pásma (tj. Pokud je hodnota deserializována v jiném systému ve stejném časovém pásmu, tato hodnota stále jednoznačně identifikuje jediný bod v čase). Mimo místní časové pásmo může mít tato <xref:System.DateTime> hodnota více výkladů. Pokud je <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>vlastnost hodnoty, je ještě méně přenosná: je nyní nejednoznačná v rámci stejného časového pásma a případně i ve stejném systému, ve kterém byla poprvé serializována. Pouze pokud <xref:System.DateTime> hodnota představuje UTC, tato hodnota jednoznačně identifikuje jediný bod v čase bez ohledu na systém nebo časové pásmo, ve kterém je hodnota použita.

> [!IMPORTANT]
> Při ukládání nebo sdílení <xref:System.DateTime> dat by se měla použít UTC <xref:System.DateTime> a <xref:System.DateTime.Kind%2A> vlastnost hodnoty by měla být nastavená na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

<xref:System.DateTimeOffset> Struktura představuje hodnotu data a času spolu s posunem, který označuje, jak velká hodnota se liší od času UTC. Proto hodnota vždy jednoznačně identifikuje jediný bod v čase.

Typ zahrnuje všechny funkce <xref:System.DateTime> typu společně s vědomím časového pásma. <xref:System.DateTimeOffset> To je vhodné pro aplikace, které provedly následující akce:

* Jedinečně a jednoznačně identifikují jediný bod v čase. <xref:System.DateTimeOffset> Typ lze použít k jednoznačnému definování významu "nyní", k protokolování časů transakcí, k protokolování časů události systému nebo aplikace a k záznamu časů vytváření a úprav souborů.

* Proveďte obecné aritmetické operace data a času.

* Zachovejte více souvisejících časů, pokud jsou tyto časy uloženy jako dvě samostatné hodnoty nebo jako dva členy struktury.

> [!NOTE]
> Tato použití pro <xref:System.DateTimeOffset> hodnoty jsou mnohem častější než u <xref:System.DateTime> hodnot. V důsledku <xref:System.DateTimeOffset> toho by se měl považovat za výchozí typ data a času pro vývoj aplikací.

<xref:System.DateTimeOffset> Hodnota není svázána s konkrétním časovým pásmem, ale může pocházet z celé řady časových pásem. Pro ilustraci tohoto příkladu obsahuje následující příklad časová pásma, do kterých může patřit určitý <xref:System.DateTimeOffset> počet hodnot (včetně místního tichomořského času).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Výstup ukazuje, že každá hodnota data a času v tomto příkladu může patřit alespoň do tří různých časových pásem. <xref:System.DateTimeOffset> Hodnota 6/10/2007 ukazuje, že pokud hodnota data a času představuje letní čas, jeho posun od času UTC ještě nutně neodpovídá základnímu posunu UTC počátečního časového pásma nebo k posunu od času UTC, který se nachází v jeho zobrazovaném názvu. To znamená, že vzhledem k tomu <xref:System.DateTimeOffset> , že jedna hodnota není pevně spojená s časovým pásmem, nemůže odrážet přechod časového pásma do a z letního času. To může být obzvláště problematické, pokud se k manipulaci s <xref:System.DateTimeOffset> hodnotou používá aritmetickí data a času. (Pro diskuzi o tom, jak provádět aritmetické operace s daty a časy způsobem, který bere v úvahu pravidla úpravy časového pásma, najdete v tématu [provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>Struktura TimeSpan

<xref:System.TimeSpan> Struktura představuje časový interval. Mezi dvě Typická použití patří:

* Odráží časový interval mezi dvěma hodnotami data a času. Například odečtením jedné <xref:System.DateTime> hodnoty z jiné <xref:System.TimeSpan> vrátí hodnotu.

* Měření uplynulého času. Například <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> vlastnost <xref:System.Diagnostics.Stopwatch> vrací hodnotu, která odráží časový interval, který uplynul od volání jedné z metod, která začíná měřit uplynulý čas. <xref:System.TimeSpan>

Hodnotu lze použít také jako náhradu <xref:System.DateTime> hodnoty, pokud tato hodnota odráží čas bez odkazů na konkrétní den. <xref:System.TimeSpan> Toto použití je podobné <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> vlastnostem a, která vrací hodnotu,kterápředstavuječasbezodkazovánínadatum.<xref:System.TimeSpan> <xref:System.TimeSpan> Struktura může například sloužit ke znázornění každodenního otevření nebo ukončení obchodu nebo může být použita k vyjádření času, kdy dojde k jakékoli běžné události.

Následující příklad definuje `StoreInfo` strukturu, která zahrnuje <xref:System.TimeSpan> objekty pro ukládání počátečních a koncových časů a také <xref:System.TimeZoneInfo> objekt, který představuje časové pásmo obchodu. Struktura také obsahuje dvě metody `IsOpenNow` a `IsOpenAt`, která označuje, zda je úložiště otevřeno v čase určeném uživatelem, který se předpokládá v místním časovém pásmu.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Strukturu pak může používat klientský kód podobný následujícímu.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Třída TimeZoneInfo

<xref:System.TimeZoneInfo> Třída představuje jakékoli časové pásmo země a umožňuje převod jakéhokoli data a času v jednom časovém pásmu na jeho ekvivalent v jiném časovém pásmu. <xref:System.TimeZoneInfo> Třída umožňuje pracovat s daty a časy, aby každá hodnota data a času jednoznačně identifikovala jediný bod v čase. <xref:System.TimeZoneInfo> Třída je také rozšiřitelná. I když závisí na informacích o časovém pásmu, které jsou k dispozici pro systémy Windows a definované v registru, podporuje vytváření vlastních časových pásem. Podporuje také serializaci a deserializaci informací o časovém pásmu.

V některých případech může použití úplné výhody <xref:System.TimeZoneInfo> třídy vyžadovat další vývojovou práci. Pokud hodnoty data a času nejsou pevně spojeny s časovými pásmy, ke kterým patří, je vyžadována další práce. Pokud vaše aplikace neposkytuje nějaký mechanismus pro propojení data a času s přidruženým časovým pásmem, je možné, že konkrétní hodnota data a času se stane nepřidruženým k časovému pásmu. Jednou z metod propojení těchto informací je definování třídy nebo struktury, která obsahuje hodnotu data a času a souvisejícího objektu časového pásma.

Využití výhod časových pásem v rozhraní .NET je možné pouze v případě, že časové pásmo, do kterého patří hodnota data a času, je známo při vytváření instance objektu data a času. To se často nejedná o případ, zejména v webových nebo síťových aplikacích.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
