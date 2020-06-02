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
ms.openlocfilehash: 86602cd6e662b1b1057832247babc558ef67b79f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276930"
---
# <a name="dates-times-and-time-zones"></a>Data, časy a časová pásma

Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:

* <xref:System.TimeZone>

  Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC). Funkčnost <xref:System.TimeZone> třídy je převážně nahrazena <xref:System.TimeZoneInfo> třídou.

* <xref:System.TimeZoneInfo>

  Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný. Pro nový vývoj použijte <xref:System.TimeZoneInfo> třídu namísto <xref:System.TimeZone> třídy.

* <xref:System.DateTimeOffset>

  Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý. <xref:System.DateTimeOffset>Struktura kombinuje hodnotu data a času s posunem času od času UTC. Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase. Díky tomu je <xref:System.DateTimeOffset> hodnota lépe přenosná z jednoho počítače na jiný než <xref:System.DateTime> hodnota.

Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.

## <a name="in-this-section"></a>V této části

[Přehled časového pásma](time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.

[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](choosing-between-datetime.md) Popisuje, kdy použít <xref:System.DateTime> typy, a <xref:System.DateTimeOffset> <xref:System.TimeZoneInfo> při práci s daty data a času.

[Hledání časových pásem definovaných v místním systému](finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.

[Postupy: zobrazení výčtu časových pásem v počítači](enumerate-time-zones.md) Poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.

[Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu](access-utc-and-local.md) Popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu.

[Postupy: vytvoření instance objektu TimeZoneInfo](instantiate-time-zone-info.md) Popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z registru místního systému.

[Vytvoření instance objektu DateTimeOffset](instantiating-a-datetimeoffset-object.md) Popisuje způsoby <xref:System.DateTimeOffset> , kterými lze vytvořit instanci objektu, a způsoby, jak <xref:System.DateTime> lze hodnotu převést na <xref:System.DateTimeOffset> hodnotu.

[Postupy: vytváření časových pásem bez pravidel úpravy](create-time-zones-without-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.

[Postupy: vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.

[Ukládání a obnova časových pásem](saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.

[Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md) Popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.

[Postupy: Obnovení časových pásem z integrovaného prostředku](restore-time-zones-from-an-embedded-resource.md) Popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.

[Provádění aritmetických operací s daty a časy](performing-arithmetic-operations.md) Popisuje problémy, které jsou součástí přidávání, odečítání a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnot.

[Postupy: používání časových pásem v aritmetickém datu a čase](use-time-zones-in-arithmetic.md) Popisuje, jak provést aritmetické operace s datem a časem, které odráží pravidla úpravy v časovém pásmu.

[Převod mezi DateTime a DateTimeOffset](converting-between-datetime-and-offset.md) Popisuje, jak převést <xref:System.DateTime> hodnoty mezi a <xref:System.DateTimeOffset> .

[Převádění časů mezi časovými pásmy](converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.

[Postupy: řešení dvojznačných časů](resolve-ambiguous-times.md) Popisuje, jak vyřešit dvojznačný čas tak, že ho namapujete na standardní čas časového pásma.

[Postupy: převod nejednoznačných časů uživatelů](let-users-resolve-ambiguous-times.md) Popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.

## <a name="reference"></a>Reference

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
