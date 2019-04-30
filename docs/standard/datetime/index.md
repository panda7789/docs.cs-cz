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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819701"
---
# <a name="dates-times-and-time-zones"></a>Data, časy a časová pásma

Kromě základních <xref:System.DateTime> strukturu, rozhraní .NET obsahuje následující třídy, které podporují práce s časovými pásmy:

* <xref:System.TimeZone>

  Tato třída slouží k práci s místní časové pásmo systému a zóně koordinovaný univerzální čas (UTC). Funkce <xref:System.TimeZone> třídy je nahrazena do značné míry <xref:System.TimeZoneInfo> třídy.

* <xref:System.TimeZoneInfo>

  Tato třída slouží k práci s časovým pásmem, předdefinovaná v systému, chcete-li vytvořit nové časových pásem a snadno převést data a časy z jedné časové pásmo na jiný. Pro vývoj nových projektů, použijte <xref:System.TimeZoneInfo> místo na třídě <xref:System.TimeZone> třídy.

* <xref:System.DateTimeOffset>

  Tuto strukturu použijte pro práci s daty a časy jejíž posun (nebo rozdílu) od času UTC je známý. <xref:System.DateTimeOffset> Struktura kombinuje datum a čas s daným časovým posun od času UTC. Z důvodu jeho vztah k času UTC, k jednotlivým datum a čas hodnota jednoznačně identifikuje jediný bod v čase. Díky tomu <xref:System.DateTimeOffset> větší přenositelnost z jednoho počítače do jiného než hodnota <xref:System.DateTime> hodnotu.

Tato část dokumentace obsahuje informace, které potřebujete pro práci s časovými pásmy a k vytváření aplikací pracujících s časové pásmo, které můžete převést kalendářní data a časy z jednoho časového pásma na jiný.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md) popisuje terminologie, koncepty a problémy týkající se vytváření aplikací pracujících s časové pásmo.

[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) popisuje použití <xref:System.DateTime>, <xref:System.DateTimeOffset>, a <xref:System.TimeZoneInfo> typy při práci s data a času.

[Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) popisuje způsob vytvoření výčtu časových pásem nalezených v místním systému.

[Postupy: Vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md) poskytuje příklady, které vytvoření výčtu časových pásem definovaných v registru počítače a, která umožní uživatelům vybrat ze seznamu předdefinovaných časové pásmo.

[Postupy: Přístup k předdefinované objekty UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md) popisuje, jak získat přístup k koordinovaný světový čas a místním časovém pásmu.

[Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z místního systémového registru.

[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) popisuje způsoby <xref:System.DateTimeOffset> můžete vytvořit instanci objektu a způsoby, ve kterém <xref:System.DateTime> hodnotu lze převést na <xref:System.DateTimeOffset> hodnotu.

[Postupy: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo nepodporuje přechod do a z letního času.

[Postupy: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, který podporuje jeden nebo více přechody do a z letního času.

[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časové pásmo a ukazuje některé scénáře, ve kterých je možné tyto funkce.

[Postupy: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložte své informace do souboru prostředků.

[Postupy: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastního časového pásma, které byly uloženy do souboru vloženého prostředku.

[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) popisuje problémy přičítání, odčítání a porovnání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.

[Postupy: Používání časových pásem v aritmetice kalendářních a časových](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) popisuje, jak provádět aritmetika data a času, která odráží pravidla úpravy časového pásma.

[Převádění mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) popisuje, jak převést mezi <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.

[Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) popisuje, jak převést časy z jednoho časového pásma.

[Postupy: Řešení nejednoznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit nejednoznačný čas tak, že mapování na časové pásmo (běžný čas).

[Postupy: Umožnit uživatelům řešení nejednoznačných časových údajů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) popisuje, jak může uživatel určit mapování mezi nejednoznačný místní čas a koordinovaný světový čas.

## <a name="reference"></a>Odkaz

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
