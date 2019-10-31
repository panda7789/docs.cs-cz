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
ms.openlocfilehash: 5425d94daf8ab023bef4a1a68f06d5c276499825
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132581"
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

Rozhraní .NET zahrnuje typy <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>a <xref:System.TimeZoneInfo>, které lze použít k sestavování aplikací pracujících s daty a časy.

> [!NOTE]
> Toto téma se nezabývá <xref:System.TimeZone>, protože jeho funkce jsou skoro zcela začleněné do <xref:System.TimeZoneInfo> třídy. Kdykoli je to možné, použijte třídu <xref:System.TimeZoneInfo> namísto <xref:System.TimeZone> třídy.

## <a name="the-datetime-structure"></a>Struktura DateTime

Hodnota <xref:System.DateTime> definuje konkrétní datum a čas. Obsahuje vlastnost <xref:System.DateTime.Kind%2A>, která poskytuje omezené informace o časovém pásmu, do kterého patří datum a čas. Hodnota <xref:System.DateTimeKind> vrácená vlastností <xref:System.DateTime.Kind%2A> označuje, zda <xref:System.DateTime> hodnota představuje místní čas (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), koordinovaný světový čas (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) nebo nespecifikovaný čas (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

Struktura <xref:System.DateTime> je vhodná pro aplikace, které mají následující:

- Pracují pouze s kalendářními daty.

- Pracujte pouze s časy.

- Pracujte s abstraktními daty a časy.

- Pracujte s daty a časy, pro které chybí informace o časovém pásmu.

- Pracovat pouze s časovými údaji a časem UTC.

- Načte informace o datu a čase ze zdrojů mimo rozhraní .NET, jako jsou databáze SQL. Obvykle tyto zdroje ukládají informace o datu a čase v jednoduchém formátu, který je kompatibilní s <xref:System.DateTime> strukturou.

- Provádění aritmetických operací s datem a časem, ale s obecnými výsledky. Například v operaci sčítání, která přidá šest měsíců do konkrétní datum a čas, často není důležité, aby byl výsledek upraven pro letní čas.

Pokud konkrétní hodnota <xref:System.DateTime> nepředstavuje UTC, je tato hodnota data a času často nejednoznačná nebo omezená ve své přenositelnosti. Pokud například hodnota <xref:System.DateTime> představuje místní čas, je přenosné v rámci tohoto místního časového pásma (tj. Pokud je hodnota deserializována v jiném systému ve stejném časovém pásmu, tato hodnota stále jednoznačně identifikuje jediný bod v čase). Mimo místní časové pásmo může mít <xref:System.DateTime> hodnota více výkladů. Je-li vlastnost <xref:System.DateTime.Kind%2A> hodnoty <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, je ještě méně přenosná: je nyní nejednoznačná v rámci stejného časového pásma a případně i ve stejném systému, ve kterém byla poprvé serializována. Pouze pokud <xref:System.DateTime> hodnota představuje UTC, tato hodnota jednoznačně identifikuje jediný bod v čase bez ohledu na systém nebo časové pásmo, ve kterém je hodnota použita.

> [!IMPORTANT]
> Při ukládání nebo sdílení <xref:System.DateTime> dat by se měla použít UTC a vlastnost <xref:System.DateTime.Kind%2A> <xref:System.DateTime> hodnoty by měla být nastavená na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

Struktura <xref:System.DateTimeOffset> představuje hodnotu data a času spolu s posunem, který označuje, jak velká hodnota se liší od času UTC. Proto hodnota vždy jednoznačně identifikuje jediný bod v čase.

Typ <xref:System.DateTimeOffset> zahrnuje všechny funkce <xref:System.DateTime> typu společně s vědomím časového pásma. To je vhodné pro aplikace, které provedly následující akce:

- Jedinečně a jednoznačně identifikují jediný bod v čase. Typ <xref:System.DateTimeOffset> lze použít k jednoznačnému definování významu "nyní", k protokolování časů transakcí, k protokolování časů událostí systému nebo aplikace a k záznamu časů vytváření a úprav souborů.

- Proveďte obecné aritmetické operace data a času.

- Zachovejte více souvisejících časů, pokud jsou tyto časy uloženy jako dvě samostatné hodnoty nebo jako dva členy struktury.

> [!NOTE]
> Tato použití pro <xref:System.DateTimeOffset> hodnoty jsou mnohem častější než u <xref:System.DateTime>ch hodnot. V důsledku toho by <xref:System.DateTimeOffset> mělo být považováno za výchozí typ data a času pro vývoj aplikací.

Hodnota <xref:System.DateTimeOffset> není vázána na konkrétní časové pásmo, ale může pocházet z celé řady časových pásem. Pro ilustraci tohoto příkladu obsahuje následující příklad časová pásma, do kterých může patřit řada <xref:System.DateTimeOffset>ch hodnot (včetně místního tichomořského času).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Výstup ukazuje, že každá hodnota data a času v tomto příkladu může patřit alespoň do tří různých časových pásem. Hodnota <xref:System.DateTimeOffset> 6/10/2007 ukazuje, že pokud hodnota data a času představuje letní čas, jeho posun od času UTC ještě nutně neodpovídá základnímu posunu UTC prvotního časového pásma nebo k posunu od času UTC, který se nachází v jeho zobrazovaném názvu. To znamená, že vzhledem k tomu, že jedna hodnota <xref:System.DateTimeOffset> není pevně spojena s časovým pásmem, nemůže odrážet přechod časového pásma do a z letního času. To může být obzvláště problematické, pokud se k manipulaci s <xref:System.DateTimeOffset> hodnota používá aritmetickí data a času. Diskuzi o tom, jak provádět aritmetické operace s daty a časy způsobem, který bere v úvahu pravidla úpravy časového pásma, najdete v tématu [provádění aritmetických operací s daty a časy](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>Struktura TimeSpan

Struktura <xref:System.TimeSpan> představuje časový interval. Mezi dvě Typická použití patří:

- Odráží časový interval mezi dvěma hodnotami data a času. Například odečtením jedné <xref:System.DateTime> hodnoty z jiné vrátí hodnotu <xref:System.TimeSpan>.

- Měření uplynulého času. Například vlastnost <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> vrací hodnotu <xref:System.TimeSpan>, která odráží časový interval, který uplynul od volání jedné z <xref:System.Diagnostics.Stopwatch> metod, která začíná měřit uplynulý čas.

Hodnotu <xref:System.TimeSpan> lze také použít jako náhradu hodnoty <xref:System.DateTime>, pokud tato hodnota odráží čas bez odkazu na konkrétní den. Toto použití je podobné vlastnostem <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>, která vrací <xref:System.TimeSpan>ou hodnotu, která představuje čas bez odkazování na datum. Například struktura <xref:System.TimeSpan> může sloužit ke znázornění každodenního otevírání nebo zavírání obchodu, nebo může být použita k vyjádření času, kdy dojde k jakékoli běžné události.

Následující příklad definuje strukturu `StoreInfo`, která zahrnuje objekty <xref:System.TimeSpan> pro ukládání počátečních a koncových časů a také objekt <xref:System.TimeZoneInfo>, který představuje časové pásmo obchodu. Struktura také obsahuje dvě metody `IsOpenNow` a `IsOpenAt`, které označují, zda je úložiště otevřeno v čase určeném uživatelem, který se předpokládá v místním časovém pásmu.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

Strukturu `StoreInfo` pak může používat klientský kód podobný následujícímu.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>Třída TimeZoneInfo

Třída <xref:System.TimeZoneInfo> představuje jakékoli časové pásmo země a umožňuje převod veškerého data a času v jednom časovém pásmu na jeho ekvivalent v jiném časovém pásmu. Třída <xref:System.TimeZoneInfo> umožňuje pracovat s daty a časy, aby každá hodnota data a času jednoznačně identifikovala jediný bod v čase. Třída <xref:System.TimeZoneInfo> je také rozšiřitelná. I když závisí na informacích o časovém pásmu, které jsou k dispozici pro systémy Windows a definované v registru, podporuje vytváření vlastních časových pásem. Podporuje také serializaci a deserializaci informací o časovém pásmu.

V některých případech může plně využít výhod <xref:System.TimeZoneInfo> třídy k dalšímu vývojovému fungování. Pokud hodnoty data a času nejsou pevně spojeny s časovými pásmy, ke kterým patří, je vyžadována další práce. Pokud vaše aplikace neposkytuje nějaký mechanismus pro propojení data a času s přidruženým časovým pásmem, je možné, že konkrétní hodnota data a času se stane nepřidruženým k časovému pásmu. Jednou z metod propojení těchto informací je definování třídy nebo struktury, která obsahuje hodnotu data a času a souvisejícího objektu časového pásma.

Využití výhod časových pásem v rozhraní .NET je možné pouze v případě, že časové pásmo, do kterého patří hodnota data a času, je známo při vytváření instance objektu data a času. To se často nejedná o případ, zejména v webových nebo síťových aplikacích.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
