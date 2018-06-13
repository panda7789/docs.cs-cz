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
ms.openlocfilehash: 368884e7f61f4504c8ca714165c543b19b3a1171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578258"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo

Aplikace .NET, které používají informace o datu a času jsou velmi rozdílné a tyto informace můžete použít několika způsoby. Více běžná použití služby informace o datu a času zahrnoval jednu či více z následujících akcí:

* Tak, aby odrážela pouze datum, tak, že informace o času není důležité.

* Tak, aby odrážela pouze po dobu, tak, že informace o datu není důležité.

* Tak, aby odrážela abstraktní datum a čas, který není vázaný na určitém čase a místě (například většina obchodů mezinárodních řetězců otevřete ve všední dny v 9:00).

* Pokud chcete načíst informace o datu a času ze zdrojů mimo rozhraní .NET, obvykle datum a čas informace se uloží v jednoduchou datový typ.

* Jedinečně a jednoznačně identifikovat jediný bod v čase. Některé aplikace vyžadují, aby datum a čas být jednoznačné pouze na hostitelském systému. jiné vyžadují, aby byly jednoznačné mezi systémy (to znamená, datum serializované na jednom systému může být srozumitelně deserializovat a použít na jiném systému kdekoliv ve světě).

* Zachovat více souvisejících časů (například žadatele místní čas a čas potvrzení serveru pro webové žádosti).

* K provedení datum a čas aritmetické, případně s výsledkem jedinečně a jednoznačně identifikující jediný bod v čase.

Zahrnuje rozhraní .NET <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, a <xref:System.TimeZoneInfo> typy, které můžete použít k vytváření aplikací, které pracují s daty a časy.

> [!NOTE]
> Toto téma nepopisuje čtvrtý typ <xref:System.TimeZone>, protože jeho funkce je téměř úplně obsažena v <xref:System.TimeZoneInfo> třídy. Kdykoli je to možné, vývojáři využít <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> třídy.

## <a name="the-datetime-structure"></a>Struktura data a času

A <xref:System.DateTime> hodnota definuje určité datum a čas. Obsahuje <xref:System.DateTime.Kind%2A> vlastnost, která poskytuje omezené informace o časovém pásmu, do které toto datum a čas patří. <xref:System.DateTimeKind> Hodnoty vrácené <xref:System.DateTime.Kind%2A> vlastnost udává, zda <xref:System.DateTime> hodnota představuje místní čas (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), koordinovaný světový čas (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), nebo nespecifikovaný čas (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

<xref:System.DateTime> Struktura je vhodný pro aplikace, které postupujte takto:

* Pracovat pouze s daty.

* Pracovat pouze s časy.

* Spolupracovat s abstraktní data a časy.

* Práce s daty a časy pro časové pásmo, které chybí informace.

* Spolupracovat s UTC data a časy jenom.

* Ze zdroje mimo .NET, např. databází SQL načíst informace o datu a času. Obvykle se tyto zdroje ukládat informace o datu a času v jednoduchém formátu, který je kompatibilní s <xref:System.DateTime> struktura.

* Proveďte datum a čas aritmetické, ale jsou problémem s obecné výsledky. Například v operaci přidání, která přidá šest měsíců určité datum a čas, je často není důležité jestli je výsledek nezohledňuje letní čas.

Pokud určitý <xref:System.DateTime> hodnota představuje UTC, datum a čas hodnota je často dvojznačná nebo omezená v přenositelnosti. Například pokud <xref:System.DateTime> hodnota představuje místní čas, je přenosná v rámci této místním časovém pásmu (Pokud je hodnota deserializovat v jiném systému ve stejném časovém pásmu, že hodnota stále jednoznačně identifikuje jediný bod v čase). Mimo místní časové pásmo, které <xref:System.DateTime> value může mít několik interpretace. Pokud hodnota <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, je i méně přenosná: Nyní je dvojznačná ve stejném časovém pásmu a případně i ve stejném systému nejprve serializovat. Pouze v případě <xref:System.DateTime> hodnota představuje čas UTC, jednoznačně identifikuje jediný bod v čase bez ohledu na to systém nebo časové pásmo, ve kterém se používá hodnota.

> [!IMPORTANT]
> Při ukládání nebo sdílení <xref:System.DateTime> data, času UTC měla být použita a <xref:System.DateTime> hodnoty <xref:System.DateTime.Kind%2A> vlastnost by měla být nastavená na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-datetimeoffset-structure"></a>Struktura DateTimeOffset

<xref:System.DateTimeOffset> Struktura reprezentuje hodnotu data a času, společně s posunem, která určuje, kolik tato hodnota se liší od času UTC. Hodnota proto vždy jednoznačně identifikuje jediný bod v čase.

<xref:System.DateTimeOffset> Typ obsahuje všechny funkce <xref:System.DateTime> typ společně s časové pásmo. Díky tomu je vhodný pro aplikace, které postupujte takto:

* Jedinečně a jednoznačně Identifikujte jediný bod v čase. <xref:System.DateTimeOffset> Typ slouží k jednoznačné definování význam "teď" pro časů transakcí protokolu, do protokolu časů událostí systému nebo aplikace a časy vytváření a úpravy záznamů souborů.

* Proveďte Obecné datum a čas aritmetické.

* Zachovat více souvisejících časů, tak dlouho, dokud jsou tyto časy uloženy jako dva samostatné hodnoty nebo dva členové struktury.

> [!NOTE]
> Tato použití pro <xref:System.DateTimeOffset> hodnoty jsou mnohem častější než pro <xref:System.DateTime> hodnoty. V důsledku toho <xref:System.DateTimeOffset> by měly být považovány za výchozí typ datum a čas pro vývoj aplikací.

A <xref:System.DateTimeOffset> hodnota není vázaný na konkrétní časové pásmo, ale může pocházet z celé řady časových pásem. Pro znázornění je následující příklad vypíše časových pásem, ke které řadu <xref:System.DateTimeOffset> můžou patřit hodnot (včetně místní Tichomořský běžný čas).

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

Výstup ukazuje, že každý datum a čas hodnotu v tomto příkladu může patřit do alespoň tři různé časová pásma. <xref:System.DateTimeOffset> Hodnotu 6/10/2007 ukazuje, že pokud hodnota data a času představuje letní čas, její posun od času UTC odpovídá i nemusí výchozí časové pásmo základní časový posun nebo posun od času UTC v jeho zobrazovaný název nalezen. To znamená, že, protože jeden <xref:System.DateTimeOffset> hodnota není pevně spojená s časovým pásmem, nemůže odrážet časové pásmo přechod do a z letní čas. To může být obzvláště problematické, pokud datum a čas aritmetické se používá k manipulaci <xref:System.DateTimeOffset> hodnotu. (Informace o tom, jak provést datum a čas aritmetické způsobem, který bere v úvahu pravidla úpravy časového pásma naleznete v [provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).)

## <a name="the-timespan-structure"></a>Struktura časové rozpětí

<xref:System.TimeSpan> Struktura představuje časovém intervalu. Jeho dva typické použití jsou:

* Odrážející časový interval mezi dvěma hodnotami data a času. Například jedna odečtením <xref:System.DateTime> hodnotu z jiné vrátí <xref:System.TimeSpan> hodnotu.

* Měření uplynulý čas. Například <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> vlastnost vrátí <xref:System.TimeSpan> hodnotu, která odráží časový interval, který uplynul od volání mezi <xref:System.Diagnostics.Stopwatch> metody, které začne měření uplynulý čas.

A <xref:System.TimeSpan> hodnotu lze také k nahrazení <xref:System.DateTime> hodnotu, pokud tuto hodnotu odráží na dobu bez odkazu na určitou dobu během dne. Toto použití je podobná <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> vlastnosti, které vrací <xref:System.TimeSpan> hodnotu, která představuje čas bez odkazu na datum. Například <xref:System.TimeSpan> struktura lze použít tak, aby odrážela denní otevírání nebo uzavírací čas úložiště, nebo se může použít k reprezentování čas, kdy dojde k jakékoli regulární události.

V následujícím příkladu definuje `StoreInfo` struktura, která zahrnuje <xref:System.TimeSpan> objekty pro uložení otevření a zavření dobu, a také <xref:System.TimeZoneInfo> objekt, který reprezentuje časové pásmo úložiště. Struktura také obsahuje dvě metody, `IsOpenNow` a `IsOpenAt`, určující, zda úložiště je otevřené současně zadanou uživatelem, který se předpokládá, že se v místním časovém pásmu.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

`StoreInfo` Struktura lze kódem na straně klienta jako následující.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>TimeZoneInfo – třída

<xref:System.TimeZoneInfo> Třída představuje jakékoli časové pásmo a umožňuje převod žádné datum a čas v jednom časovém pásmu na odpovídající hodnotu v jiném časovém pásmu. <xref:System.TimeZoneInfo> Třída umožňuje pracovat s daty a časy tak, aby všechny hodnoty data a času jednoznačně identifikuje jediný bod v čase. <xref:System.TimeZoneInfo> Třída je rozšiřitelný. Ačkoli je závislá na informace o časovém pásmu poskytuje pro systémy Windows a definované v registru, podporuje vytváření vlastní časová pásma. Podporuje také serializace a deserializace informace o časovém pásmu.

V některých případech plně využít <xref:System.TimeZoneInfo> třída může vyžadovat další vývojové práci. Pokud se hodnoty data a času nejsou pevně spojená s časových pásem, do kterých patří, dále fungovat není potřeba. Pokud vaše aplikace poskytuje určitý mechanismus pro propojení datum a čas s jeho přidružené časové pásmo, je snadné pro konkrétní datum a čas hodnota oddělit od jeho časové pásmo. Jedna z metod propojení tyto informace je definovat třídu nebo strukturu, která obsahuje datum a čas hodnotu a jeho přidružený objekt časového pásma.

Využití výhod podpory časové pásmo v rozhraní .NET je možné pouze v případě, že časové pásmo, ke kterému patří hodnota data a času je známo, když je vytvořena instance tohoto objektu data a času. To často tak není, zejména v aplikacích pro Web nebo sítě.

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
