---
title: Data, časy a časová pásma
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5355666b95d75fc18d0188c978c186690ee9ccca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575424"
---
# <a name="dates-times-and-time-zones"></a>Data, časy a časová pásma

Kromě základní <xref:System.DateTime> struktura, rozhraní .NET obsahuje následující třídy, které podporují práci s časovými pásmy:

* <xref:System.TimeZone>

  Tato třída slouží k práci s místním časovém pásmu systém a zóny koordinovaný světový čas (UTC). Funkce <xref:System.TimeZone> třída je do značné míry nahrazena <xref:System.TimeZoneInfo> třídy.

* <xref:System.TimeZoneInfo>

  Tato třída slouží k práci s časovým pásmem, který je předdefinovaná v systému, chcete-li vytvořit nové časových pásem a snadno převést data a časy z jednoho časového pásma na jiný. Pro nový vývoj pomocí <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> třídy.

* <xref:System.DateTimeOffset>

  Použijte tuto strukturu pro práci s daty a doby jejíž posun (nebo rozdíl) od času UTC je známý. <xref:System.DateTimeOffset> Struktura kombinuje datum a čas se této doby posun od času UTC. Z důvodu jeho relace na UTC, jednotlivé datum a čas hodnota jednoznačně identifikuje jediný bod v čase. Díky tomu <xref:System.DateTimeOffset> víc přenosného z jednoho počítače do jiného než hodnota <xref:System.DateTime> hodnotu.

Tato část dokumentace obsahuje informace, které budete potřebovat pro práci s časových pásem a k vytvoření časová pásma si aplikace, které můžete převést data a časy z jednoho časového pásma na jiný.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy při vytváření aplikace využívající technologii časové pásmo.

[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) popisuje použití <xref:System.DateTime>, <xref:System.DateTimeOffset>, a <xref:System.TimeZoneInfo> typy při práci s daty datum a čas.

[Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) popisuje postup vytvoření výčtu časových pásem v místním systému nalezen.

[Postupy: vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md) obsahuje příklady, které vytvářejí výčet časových pásem definovaných v registru počítače a který umožní uživatelům vybrat ze seznamu předdefinovaných časové pásmo.

[Postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md) popisuje, jak získat přístup k koordinovaného světového času a místním časovém pásmu.

[Postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objekt z registru místního systému.

[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) popisuje způsoby, ve kterém <xref:System.DateTimeOffset> objekt se dá vytvořit instance a způsoby, ve kterém <xref:System.DateTime> hodnotu lze převést na <xref:System.DateTimeOffset> hodnotu.

[Postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod do a z letní čas.

[Postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, které podporuje jeden nebo více přechody do a z letní čas.

[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a ilustruje některého z následujících scénářů, ve kterých se tyto funkce lze použít.

[Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložte informace o jeho v souboru prostředků.

[Postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastního časového pásma, které byly uloženy do souboru vložený prostředek.

[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) popisuje problémy, přidání, odečtením a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.

[Postupy: používání časových pásem datum a čas aritmetické](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) popisuje, jak provést datum a čas aritmetické odráží pravidla úpravy časového pásma.

[Převádění mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) popisuje, jak pro převod mezi <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.

[Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) popisuje, jak převést časy z jednoho časového pásma.

[Postupy: řešení víceznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit nejednoznačný čas mapování na časové pásmo (běžný čas).

[Postupy: řešení víceznačných časových údajů uživatelé mohli](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) popisuje, jak může uživatel určit mapování mezi nejednoznačný místní čas a koordinovaného světového času.

## <a name="reference"></a>Odkaz

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
