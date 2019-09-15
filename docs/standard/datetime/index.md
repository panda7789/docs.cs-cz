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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="52a94-102">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="52a94-102">Dates, times, and time zones</span></span>

<span data-ttu-id="52a94-103">Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:</span><span class="sxs-lookup"><span data-stu-id="52a94-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="52a94-104">Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC).</span><span class="sxs-lookup"><span data-stu-id="52a94-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="52a94-105">Funkčnost <xref:System.TimeZone> třídy je převážně nahrazena <xref:System.TimeZoneInfo> třídou.</span><span class="sxs-lookup"><span data-stu-id="52a94-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="52a94-106">Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="52a94-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="52a94-107">Pro nový vývoj použijte <xref:System.TimeZoneInfo> třídu namísto <xref:System.TimeZone> třídy.</span><span class="sxs-lookup"><span data-stu-id="52a94-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="52a94-108">Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý.</span><span class="sxs-lookup"><span data-stu-id="52a94-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="52a94-109"><xref:System.DateTimeOffset> Struktura kombinuje hodnotu data a času s posunem času od času UTC.</span><span class="sxs-lookup"><span data-stu-id="52a94-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="52a94-110">Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="52a94-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="52a94-111">Díky tomu je <xref:System.DateTimeOffset> hodnota lépe přenosná z jednoho počítače na jiný <xref:System.DateTime> než hodnota.</span><span class="sxs-lookup"><span data-stu-id="52a94-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="52a94-112">Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="52a94-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="52a94-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52a94-113">In this section</span></span>

<span data-ttu-id="52a94-114">[Přehled časového pásma](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="52a94-114">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="52a94-115">[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Popisuje <xref:System.DateTime>, kdy použít <xref:System.TimeZoneInfo> typy, <xref:System.DateTimeOffset>a při práci s daty data a času.</span><span class="sxs-lookup"><span data-stu-id="52a94-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="52a94-116">[Hledání časových pásem definovaných v místním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.</span><span class="sxs-lookup"><span data-stu-id="52a94-116">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="52a94-117">[Postupy: Zobrazení výčtu časových pásem přítomných na](../../../docs/standard/datetime/enumerate-time-zones.md) počítači poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="52a94-117">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="52a94-118">[Postupy: Přístup k předdefinovaným objektům](../../../docs/standard/datetime/access-utc-and-local.md) UTC a místnímu časovému pásmu popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu</span><span class="sxs-lookup"><span data-stu-id="52a94-118">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="52a94-119">[Postupy: Vytvoření instance objektu](../../../docs/standard/datetime/instantiate-time-zone-info.md) TimeZoneInfo popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="52a94-119">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="52a94-120">[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Popisuje způsoby, kterými <xref:System.DateTimeOffset> lze vytvořit instanci objektu, a způsoby, jak <xref:System.DateTime> <xref:System.DateTimeOffset> lze hodnotu převést na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="52a94-120">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="52a94-121">[Postupy: Vytváření časových pásem bez pravidel](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) úprav popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.</span><span class="sxs-lookup"><span data-stu-id="52a94-121">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="52a94-122">[Postupy: Vytváření časových pásem s pravidly](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) úpravy popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.</span><span class="sxs-lookup"><span data-stu-id="52a94-122">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="52a94-123">[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.</span><span class="sxs-lookup"><span data-stu-id="52a94-123">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="52a94-124">[Postupy: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="52a94-124">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="52a94-125">[Postupy: Obnovení časových pásem z vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="52a94-125">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="52a94-126">[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) Popisuje problémy, které jsou součástí přidávání, odečítání a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnot.</span><span class="sxs-lookup"><span data-stu-id="52a94-126">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="52a94-127">[Postupy: Časová pásma v aritmetických](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) hodnotách data a času slouží k provedení aritmetického zpracování data a času, která odráží pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="52a94-127">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="52a94-128">[Převod mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Popisuje, jak převést hodnoty <xref:System.DateTime> mezi <xref:System.DateTimeOffset> a.</span><span class="sxs-lookup"><span data-stu-id="52a94-128">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="52a94-129">[Převádění časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="52a94-129">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="52a94-130">[Postupy: Řešení nejednoznačných časů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit dvojznačný čas tím, že ho namapujete na standardní čas časového pásma.</span><span class="sxs-lookup"><span data-stu-id="52a94-130">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="52a94-131">[Postupy: Umožněte uživatelům vyřešit nejednoznačné](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) časy. popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.</span><span class="sxs-lookup"><span data-stu-id="52a94-131">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="52a94-132">Reference</span><span class="sxs-lookup"><span data-stu-id="52a94-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
