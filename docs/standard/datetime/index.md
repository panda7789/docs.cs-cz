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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="16b1f-102">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="16b1f-102">Dates, times, and time zones</span></span>

<span data-ttu-id="16b1f-103">Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:</span><span class="sxs-lookup"><span data-stu-id="16b1f-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="16b1f-104">Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC).</span><span class="sxs-lookup"><span data-stu-id="16b1f-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="16b1f-105">Funkce <xref:System.TimeZone> třídy je převážně nahrazena třídou <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="16b1f-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="16b1f-106">Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="16b1f-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="16b1f-107">Pro nový vývoj použijte třídu <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b1f-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="16b1f-108">Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý.</span><span class="sxs-lookup"><span data-stu-id="16b1f-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="16b1f-109">Struktura <xref:System.DateTimeOffset> kombinuje hodnotu data a času s posunem času od času UTC.</span><span class="sxs-lookup"><span data-stu-id="16b1f-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="16b1f-110">Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="16b1f-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="16b1f-111">Tím se hodnota <xref:System.DateTimeOffset>ější přenos z jednoho počítače do jiného než hodnota <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="16b1f-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="16b1f-112">Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="16b1f-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="16b1f-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="16b1f-113">In this section</span></span>

<span data-ttu-id="16b1f-114">[Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="16b1f-114">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="16b1f-115">[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Popisuje, kdy použít typy <xref:System.DateTime>, <xref:System.DateTimeOffset>a <xref:System.TimeZoneInfo> při práci s daty data a času.</span><span class="sxs-lookup"><span data-stu-id="16b1f-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="16b1f-116">[Hledání časových pásem definovaných v místním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.</span><span class="sxs-lookup"><span data-stu-id="16b1f-116">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="16b1f-117">[Postupy: zobrazení výčtu časových pásem v počítači](../../../docs/standard/datetime/enumerate-time-zones.md) Poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="16b1f-117">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="16b1f-118">[Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu](../../../docs/standard/datetime/access-utc-and-local.md) Popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu.</span><span class="sxs-lookup"><span data-stu-id="16b1f-118">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="16b1f-119">[Postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) Popisuje, jak vytvořit instanci objektu <xref:System.TimeZoneInfo> z registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="16b1f-119">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="16b1f-120">[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Popisuje způsoby, kterými lze vytvořit instanci objektu <xref:System.DateTimeOffset>, a způsoby, jak lze hodnotu <xref:System.DateTime> převést na hodnotu <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="16b1f-120">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="16b1f-121">[Postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.</span><span class="sxs-lookup"><span data-stu-id="16b1f-121">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="16b1f-122">[Postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.</span><span class="sxs-lookup"><span data-stu-id="16b1f-122">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="16b1f-123">[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.</span><span class="sxs-lookup"><span data-stu-id="16b1f-123">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="16b1f-124">[Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="16b1f-124">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="16b1f-125">[Postupy: Obnovení časových pásem z integrovaného prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="16b1f-125">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="16b1f-126">[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) Popisuje problémy, které se podílejí na přidávání, odečítání a porovnávání hodnot <xref:System.DateTime> a <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="16b1f-126">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="16b1f-127">[Postupy: používání časových pásem v aritmetickém datu a čase](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Popisuje, jak provést aritmetické operace s datem a časem, které odráží pravidla úpravy v časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="16b1f-127">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="16b1f-128">[Převod mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Popisuje, jak převést hodnoty mezi <xref:System.DateTime> a <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="16b1f-128">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="16b1f-129">[Převádění časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="16b1f-129">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="16b1f-130">[Postupy: řešení dvojznačných časů](../../../docs/standard/datetime/resolve-ambiguous-times.md) Popisuje, jak vyřešit dvojznačný čas tak, že ho namapujete na standardní čas časového pásma.</span><span class="sxs-lookup"><span data-stu-id="16b1f-130">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="16b1f-131">[Postupy: převod nejednoznačných časů uživatelů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.</span><span class="sxs-lookup"><span data-stu-id="16b1f-131">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="16b1f-132">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16b1f-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
