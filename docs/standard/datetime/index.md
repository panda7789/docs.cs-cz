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
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991289"
---
# <a name="dates-times-and-time-zones"></a>Data, časy a časová pásma

Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:

* <xref:System.TimeZone>

  Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC). Funkčnost <xref:System.TimeZone> třídy je převážně nahrazena <xref:System.TimeZoneInfo> třídou.

* <xref:System.TimeZoneInfo>

  Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný. Pro nový vývoj použijte <xref:System.TimeZoneInfo> třídu namísto <xref:System.TimeZone> třídy.

* <xref:System.DateTimeOffset>

  Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý. <xref:System.DateTimeOffset> Struktura kombinuje hodnotu data a času s posunem času od času UTC. Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase. Díky tomu je <xref:System.DateTimeOffset> hodnota lépe přenosná z jednoho počítače na jiný <xref:System.DateTime> než hodnota.

Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.

[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Popisuje <xref:System.DateTime>, kdy použít <xref:System.TimeZoneInfo> typy, <xref:System.DateTimeOffset>a při práci s daty data a času.

[Hledání časových pásem definovaných v místním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.

[Postupy: Zobrazení výčtu časových pásem přítomných na](../../../docs/standard/datetime/enumerate-time-zones.md) počítači poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.

[Postupy: Přístup k předdefinovaným objektům](../../../docs/standard/datetime/access-utc-and-local.md) UTC a místnímu časovému pásmu popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu

[Postupy: Vytvoření instance objektu](../../../docs/standard/datetime/instantiate-time-zone-info.md) TimeZoneInfo popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z registru místního systému.

[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Popisuje způsoby, kterými <xref:System.DateTimeOffset> lze vytvořit instanci objektu, a způsoby, jak <xref:System.DateTime> <xref:System.DateTimeOffset> lze hodnotu převést na hodnotu.

[Postupy: Vytváření časových pásem bez pravidel](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) úprav popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.

[Postupy: Vytváření časových pásem s pravidly](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) úpravy popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.

[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.

[Postupy: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.

[Postupy: Obnovení časových pásem z vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.

[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) Popisuje problémy, které jsou součástí přidávání, odečítání a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnot.

[Postupy: Časová pásma v aritmetických](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) hodnotách data a času slouží k provedení aritmetického zpracování data a času, která odráží pravidla úpravy časového pásma.

[Převod mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Popisuje, jak převést hodnoty <xref:System.DateTime> mezi <xref:System.DateTimeOffset> a.

[Převádění časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.

[Postupy: Řešení nejednoznačných časů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit dvojznačný čas tím, že ho namapujete na standardní čas časového pásma.

[Postupy: Umožněte uživatelům vyřešit nejednoznačné](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) časy. popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.

## <a name="reference"></a>Reference

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
