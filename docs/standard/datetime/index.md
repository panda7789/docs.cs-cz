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
ms.openlocfilehash: d46b3cdbddeb1b4e28b7108e7925bd3f086498d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122302"
---
# <a name="dates-times-and-time-zones"></a>Data, časy a časová pásma

Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:

* <xref:System.TimeZone>

  Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC). Funkce <xref:System.TimeZone> třídy je převážně nahrazena třídou <xref:System.TimeZoneInfo>.

* <xref:System.TimeZoneInfo>

  Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný. Pro nový vývoj použijte třídu <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> třídy.

* <xref:System.DateTimeOffset>

  Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý. Struktura <xref:System.DateTimeOffset> kombinuje hodnotu data a času s posunem času od času UTC. Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase. Tím se hodnota <xref:System.DateTimeOffset>ější přenos z jednoho počítače do jiného než hodnota <xref:System.DateTime>.

Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.

[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Popisuje, kdy použít typy <xref:System.DateTime>, <xref:System.DateTimeOffset>a <xref:System.TimeZoneInfo> při práci s daty data a času.

[Hledání časových pásem definovaných v místním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.

[Postupy: zobrazení výčtu časových pásem v počítači](../../../docs/standard/datetime/enumerate-time-zones.md) Poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.

[Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu](../../../docs/standard/datetime/access-utc-and-local.md) Popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu.

[Postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) Popisuje, jak vytvořit instanci objektu <xref:System.TimeZoneInfo> z registru místního systému.

[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Popisuje způsoby, kterými lze vytvořit instanci objektu <xref:System.DateTimeOffset>, a způsoby, jak lze hodnotu <xref:System.DateTime> převést na hodnotu <xref:System.DateTimeOffset>.

[Postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.

[Postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.

[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.

[Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.

[Postupy: Obnovení časových pásem z integrovaného prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.

[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) Popisuje problémy, které se podílejí na přidávání, odečítání a porovnávání hodnot <xref:System.DateTime> a <xref:System.DateTimeOffset>.

[Postupy: používání časových pásem v aritmetickém datu a čase](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Popisuje, jak provést aritmetické operace s datem a časem, které odráží pravidla úpravy v časovém pásmu.

[Převod mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Popisuje, jak převést hodnoty mezi <xref:System.DateTime> a <xref:System.DateTimeOffset>.

[Převádění časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.

[Postupy: řešení dvojznačných časů](../../../docs/standard/datetime/resolve-ambiguous-times.md) Popisuje, jak vyřešit dvojznačný čas tak, že ho namapujete na standardní čas časového pásma.

[Postupy: převod nejednoznačných časů uživatelů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.

## <a name="reference"></a>Odkaz

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
