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
ms.openlocfilehash: 0ed41d7739822d531986d65faa820ab7100c6651
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026559"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo

Aplikace .NET, které používají informace o datu a čase jsou velmi rozdílné a může pomocí těchto informací v několika způsoby. Častější používá informace o datu a času zahrnovat jeden nebo více z následujících akcí:

* Tak, aby odrážely pouze datum, tak, že informace o času není důležité.

* Tak, aby odrážely pouze čas, tak, že informace o datu není důležité.

* Aby odrážel abstraktní datum a čas, který není vázaný na určitou dobu a místě (například většina úložišť v řetěz mezinárodní otevřít ve všední dny v 9:00).

* Pokud chcete načíst informace o datu a času ze zdroje mimo rozhraní .NET, obvykle informace o datu a času se mají ukládat v jednoduché datového typu.

* Jedinečně a jednoznačně identifikovat jediný bod v čase. Některé aplikace vyžadují, aby datum a čas jednoznačný pouze v hostitelském systému. jiné vyžadují, aby byly jednoznačný napříč systémy (to znamená, že data serializovaná v jednom systému jde smysluplně deserializovat a používat v jiném systému kdekoli ve světě).

* Zachovat více souvisejících časů (například žadatele místní čas a čas serveru přijetí pro webový požadavek).

* K provedení datum a čas, aritmetické, případně s výsledkem, který jedinečně a jednoznačně identifikuje jediný bod v čase.

Zahrnuje .NET <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, a <xref:System.TimeZoneInfo> typy, které můžete použít k sestavení aplikací, které pracují s daty a časy.

> [!NOTE]
> Toto téma se nezabývá čtvrtý typ <xref:System.TimeZone>, protože jeho funkce je téměř zcela obsažena v <xref:System.TimeZoneInfo> třídy. Kdykoli je to možné, používejte vývojáři <xref:System.TimeZoneInfo> místo na třídě <xref:System.TimeZone> třídy.

## <a name="the-datetime-structure"></a>Strukturu DateTime

A <xref:System.DateTime> hodnota definuje konkrétní datum a čas. Zahrnuje <xref:System.DateTime.Kind%2A> vlastnost, která poskytuje omezené informace o časovém pásmu, do které toto datum a čas patří. <xref:System.DateTimeKind> Hodnoty vrácené <xref:System.DateTime.Kind%2A> vlastnost určuje, zda <xref:System.DateTime> hodnota představuje místní čas (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), koordinovaný univerzální čas (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), nebo nespecifikovaný čas (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Struktura je vhodná pro aplikace, které postupujte takto:

* Pracovat pouze s daty.

* Pracovat pouze s časy.

* Práce s abstraktní daty a časy.

* Práce s daty a časy pro časové pásmo, které chybí informace.

* Práce s daty UTC a časy pouze.

* Informace o datu a času načtěte ze zdroje mimo rozhraní .NET, jako jsou databáze SQL. Obvykle tyto zdroje ukládat informace o datu a času ve formátu, který je kompatibilní s jednoduchou <xref:System.DateTime> struktury.

* Proveďte datum a čas aritmetický, ale jsou problémem obecné výsledky. Například v operaci sčítání, která přidá za šest měsíců na konkrétní datum a čas, je často není důležité, jestli je výsledek upraven pro letní čas.

Pokud konkrétní <xref:System.DateTime> představuje hodnotu UTC, toto datum a čas je často nejednoznačný nebo máte jenom omezenou v jeho přenositelnost. Například pokud <xref:System.DateTime> hodnota představuje místní čas, je přenositelné v rámci této místní časové pásmo (tj. Pokud hodnota je deserializovat v jiném systému ve stejném časovém pásmu, že hodnota stále jednoznačně identifikuje jediný bod v čase). Mimo časovou zónu, která <xref:System.DateTime> hodnota může mít více interpretací. Pokud hodnota <xref:System.DateTime.Kind%2A> vlastnost <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, je i menší přenositelnost: je nyní nejednoznačný ve stejném časovém pásmu a případně i ve stejném systému nejdřív serializovat. Pouze tehdy, pokud <xref:System.DateTime> hodnota představuje čas UTC, že hodnota jednoznačně identifikuje jediný bod v čase bez ohledu na to, v systému nebo časové pásmo, ve kterém se používá hodnota.

> [!IMPORTANT]
> Při ukládání nebo sdílení <xref:System.DateTime> by měla sloužit data, UTC a <xref:System.DateTime> hodnoty <xref:System.DateTime.Kind%2A> vlastnost by měla být nastavena na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

<xref:System.DateTimeOffset> Struktura reprezentuje hodnotu data a času spolu s posunem, který označuje, kolik tato hodnota se liší od času UTC. Díky tomu se hodnota vždy jednoznačně identifikuje jediný bod v čase.

<xref:System.DateTimeOffset> Typu zahrnuje všechny funkce <xref:System.DateTime> typ spolu s časové pásmo. Díky tomu vhodné pro aplikace, které postupujte takto:

* Jedinečně a jednoznačně Identifikujte jediný bod v čase. <xref:System.DateTimeOffset> Typ slouží k jednoznačné definování význam "teď", časy transakcí protokolu, do protokolu časy událostí systému nebo aplikace a časy pro vytváření a úpravy záznamů souborů.

* Proveďte Obecné datum a čas aritmetické operace.

* Zachovat více souvisejících časů, tak dlouho, dokud tyto časy jsou uloženy jako dva samostatné hodnoty nebo jako dva členy struktury.

> [!NOTE]
> Použití pro <xref:System.DateTimeOffset> hodnoty jsou mnohem častější než u <xref:System.DateTime> hodnoty. V důsledku toho <xref:System.DateTimeOffset> by měly být považovány za výchozí typ datum a čas pro vývoj aplikací.

A <xref:System.DateTimeOffset> hodnotu objektu se neváže na konkrétní časové pásmo, ale můžou pocházet z některé z různých časových pásmech. Pro znázornění je následující příklad zobrazí seznam časových pásem, ke kterému celou řadou <xref:System.DateTimeOffset> může patřit hodnoty (včetně místních standardního tichomořského času).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Výstup ukazuje, že každé datum a čas v tomto příkladu může patřit do alespoň tří různých časových pásmech. <xref:System.DateTimeOffset> Hodnotu 6/10/2007 ukazuje, že pokud se hodnoty data a času představují letní čas, posun od času UTC odpovídá ještě nutně původní časové pásmo udává základní posun UTC nebo posun od času UTC v jeho zobrazovaného názvu nalezena. To znamená, že, protože jeden <xref:System.DateTimeOffset> hodnota není pevně spojená s časovým pásmem, nemůže odrážet časové pásmo přechodu do a z letního času. To může být obzvláště problematické, pokud aritmetice kalendářních a časových se používá k manipulaci <xref:System.DateTimeOffset> hodnotu. (Informace o tom, jak provést způsobem, který bere v úvahu pravidla úpravy časového pásma aritmetice kalendářních a časových, najdete v článku [provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>Struktury TimeSpan

<xref:System.TimeSpan> Struktura představuje časový interval. Jeho dvě typické použití jsou:

* Odráží časový interval mezi dvěma hodnotami data a času. Například jeden odečtením <xref:System.DateTime> hodnotu z jiného vrátí <xref:System.TimeSpan> hodnotu.

* Uplynulý čas měření. Například <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> vrátí vlastnost <xref:System.TimeSpan> hodnotu, která odpovídá časový interval, která uplynula od posledního volání mezi <xref:System.Diagnostics.Stopwatch> metody, které začíná měření uplynulý čas.

A <xref:System.TimeSpan> hodnotu lze také jako náhrada <xref:System.DateTime> hodnotu, pokud tato hodnota zahrnuje čas bez ohledu na určitou denní dobu. Toto použití je podobný <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> vlastnosti, které vracejí <xref:System.TimeSpan> hodnotu, která představuje čas bez ohledu na datum. Například <xref:System.TimeSpan> struktury lze použít tak, aby odrážely denní otevírací nebo uzavírací čas úložiště, nebo ji lze představují čas, kdy dojde k jakékoli normální událost.

Následující příklad definuje `StoreInfo` strukturu, která zahrnuje <xref:System.TimeSpan> objekty pro ukládání otevírací a uzavírací dobu, a také <xref:System.TimeZoneInfo> objekt, který představuje časové pásmo úložiště. Struktury také obsahuje dvě metody `IsOpenNow` a `IsOpenAt`, určující, zda úložiště je otevřený v době zadané uživatelem, který je považován za v místním časovém pásmu.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Struktura je pak možné klientským kódem, jako je následující.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo – třída

<xref:System.TimeZoneInfo> Třída reprezentuje všechny časové pásmo a umožňuje převod libovolného data a času v jednom časovém pásmu na jeho ekvivalent v jiném časovém pásmu. <xref:System.TimeZoneInfo> Třída umožňuje pracovat s daty a časy tak, aby všechny hodnoty data a času jednoznačně identifikuje jediný bod v čase. <xref:System.TimeZoneInfo> Třídy je rozšiřitelné. Přestože je závislé na informace o časovém pásmu pro systémy Windows k dispozici a definovaná v registru, podporuje vytváření vlastního časového pásma. Podporuje také serializace a deserializace informace o časovém pásmu.

V některých případech může naplno využívat <xref:System.TimeZoneInfo> třída může vyžadovat další vývojářské práce. Pokud se hodnoty data a času nejsou pevně spojená s časovými pásmy, do kterých patří, další práce je povinný. Pokud vaše aplikace poskytuje určitý mechanismus pro propojení datum a čas s časovým pásmem přidružený, je snadné pro konkrétní datum a čas oddělit od jeho časové pásmo. Jedním ze způsobů propojení těchto informací je definovat třídu nebo strukturu, která obsahuje datum a čas a jeho přidružený objekt časového pásma.

Využití výhod podpory časového pásma v rozhraní .NET je možné pouze v případě, že časové pásmo, do které patří hodnoty data a času je známo, když je vytvořena instance objektu data a času. To je často případ, zejména v aplikacích webového nebo síťového.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
