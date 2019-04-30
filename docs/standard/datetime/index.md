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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="e16b3-102">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="e16b3-102">Dates, times, and time zones</span></span>

<span data-ttu-id="e16b3-103">Kromě základních <xref:System.DateTime> strukturu, rozhraní .NET obsahuje následující třídy, které podporují práce s časovými pásmy:</span><span class="sxs-lookup"><span data-stu-id="e16b3-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="e16b3-104">Tato třída slouží k práci s místní časové pásmo systému a zóně koordinovaný univerzální čas (UTC). Funkce <xref:System.TimeZone> třídy je nahrazena do značné míry <xref:System.TimeZoneInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="e16b3-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="e16b3-105">Tato třída slouží k práci s časovým pásmem, předdefinovaná v systému, chcete-li vytvořit nové časových pásem a snadno převést data a časy z jedné časové pásmo na jiný.</span><span class="sxs-lookup"><span data-stu-id="e16b3-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="e16b3-106">Pro vývoj nových projektů, použijte <xref:System.TimeZoneInfo> místo na třídě <xref:System.TimeZone> třídy.</span><span class="sxs-lookup"><span data-stu-id="e16b3-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="e16b3-107">Tuto strukturu použijte pro práci s daty a časy jejíž posun (nebo rozdílu) od času UTC je známý.</span><span class="sxs-lookup"><span data-stu-id="e16b3-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="e16b3-108"><xref:System.DateTimeOffset> Struktura kombinuje datum a čas s daným časovým posun od času UTC.</span><span class="sxs-lookup"><span data-stu-id="e16b3-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="e16b3-109">Z důvodu jeho vztah k času UTC, k jednotlivým datum a čas hodnota jednoznačně identifikuje jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="e16b3-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="e16b3-110">Díky tomu <xref:System.DateTimeOffset> větší přenositelnost z jednoho počítače do jiného než hodnota <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e16b3-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="e16b3-111">Tato část dokumentace obsahuje informace, které potřebujete pro práci s časovými pásmy a k vytváření aplikací pracujících s časové pásmo, které můžete převést kalendářní data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="e16b3-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e16b3-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e16b3-112">In this section</span></span>

<span data-ttu-id="e16b3-113">[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md) popisuje terminologie, koncepty a problémy týkající se vytváření aplikací pracujících s časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="e16b3-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="e16b3-114">[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) popisuje použití <xref:System.DateTime>, <xref:System.DateTimeOffset>, a <xref:System.TimeZoneInfo> typy při práci s data a času.</span><span class="sxs-lookup"><span data-stu-id="e16b3-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="e16b3-115">[Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) popisuje způsob vytvoření výčtu časových pásem nalezených v místním systému.</span><span class="sxs-lookup"><span data-stu-id="e16b3-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="e16b3-116">[Postupy: Vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md) poskytuje příklady, které vytvoření výčtu časových pásem definovaných v registru počítače a, která umožní uživatelům vybrat ze seznamu předdefinovaných časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="e16b3-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="e16b3-117">[Postupy: Přístup k předdefinované objekty UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md) popisuje, jak získat přístup k koordinovaný světový čas a místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="e16b3-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="e16b3-118">[Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z místního systémového registru.</span><span class="sxs-lookup"><span data-stu-id="e16b3-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="e16b3-119">[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) popisuje způsoby <xref:System.DateTimeOffset> můžete vytvořit instanci objektu a způsoby, ve kterém <xref:System.DateTime> hodnotu lze převést na <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e16b3-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="e16b3-120">[Postupy: Vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo nepodporuje přechod do a z letního času.</span><span class="sxs-lookup"><span data-stu-id="e16b3-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="e16b3-121">[Postupy: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, který podporuje jeden nebo více přechody do a z letního času.</span><span class="sxs-lookup"><span data-stu-id="e16b3-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="e16b3-122">[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časové pásmo a ukazuje některé scénáře, ve kterých je možné tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="e16b3-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="e16b3-123">[Postupy: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložte své informace do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="e16b3-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="e16b3-124">[Postupy: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastního časového pásma, které byly uloženy do souboru vloženého prostředku.</span><span class="sxs-lookup"><span data-stu-id="e16b3-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="e16b3-125">[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) popisuje problémy přičítání, odčítání a porovnání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e16b3-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="e16b3-126">[Postupy: Používání časových pásem v aritmetice kalendářních a časových](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) popisuje, jak provádět aritmetika data a času, která odráží pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="e16b3-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="e16b3-127">[Převádění mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) popisuje, jak převést mezi <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e16b3-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="e16b3-128">[Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) popisuje, jak převést časy z jednoho časového pásma.</span><span class="sxs-lookup"><span data-stu-id="e16b3-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="e16b3-129">[Postupy: Řešení nejednoznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit nejednoznačný čas tak, že mapování na časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="e16b3-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="e16b3-130">[Postupy: Umožnit uživatelům řešení nejednoznačných časových údajů](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) popisuje, jak může uživatel určit mapování mezi nejednoznačný místní čas a koordinovaný světový čas.</span><span class="sxs-lookup"><span data-stu-id="e16b3-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="e16b3-131">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e16b3-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
