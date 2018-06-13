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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="c8666-102">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="c8666-102">Dates, times, and time zones</span></span>

<span data-ttu-id="c8666-103">Kromě základní <xref:System.DateTime> struktura, rozhraní .NET obsahuje následující třídy, které podporují práci s časovými pásmy:</span><span class="sxs-lookup"><span data-stu-id="c8666-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="c8666-104">Tato třída slouží k práci s místním časovém pásmu systém a zóny koordinovaný světový čas (UTC). Funkce <xref:System.TimeZone> třída je do značné míry nahrazena <xref:System.TimeZoneInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8666-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="c8666-105">Tato třída slouží k práci s časovým pásmem, který je předdefinovaná v systému, chcete-li vytvořit nové časových pásem a snadno převést data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="c8666-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="c8666-106">Pro nový vývoj pomocí <xref:System.TimeZoneInfo> místo <xref:System.TimeZone> třídy.</span><span class="sxs-lookup"><span data-stu-id="c8666-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="c8666-107">Použijte tuto strukturu pro práci s daty a doby jejíž posun (nebo rozdíl) od času UTC je známý.</span><span class="sxs-lookup"><span data-stu-id="c8666-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="c8666-108"><xref:System.DateTimeOffset> Struktura kombinuje datum a čas se této doby posun od času UTC.</span><span class="sxs-lookup"><span data-stu-id="c8666-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="c8666-109">Z důvodu jeho relace na UTC, jednotlivé datum a čas hodnota jednoznačně identifikuje jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="c8666-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="c8666-110">Díky tomu <xref:System.DateTimeOffset> víc přenosného z jednoho počítače do jiného než hodnota <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c8666-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="c8666-111">Tato část dokumentace obsahuje informace, které budete potřebovat pro práci s časových pásem a k vytvoření časová pásma si aplikace, které můžete převést data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="c8666-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c8666-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c8666-112">In this section</span></span>

<span data-ttu-id="c8666-113">[Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md) Popisuje terminologii, koncepty a problémy při vytváření aplikace využívající technologii časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="c8666-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="c8666-114">[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) popisuje použití <xref:System.DateTime>, <xref:System.DateTimeOffset>, a <xref:System.TimeZoneInfo> typy při práci s daty datum a čas.</span><span class="sxs-lookup"><span data-stu-id="c8666-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="c8666-115">[Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) popisuje postup vytvoření výčtu časových pásem v místním systému nalezen.</span><span class="sxs-lookup"><span data-stu-id="c8666-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="c8666-116">[Postupy: vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md) obsahuje příklady, které vytvářejí výčet časových pásem definovaných v registru počítače a který umožní uživatelům vybrat ze seznamu předdefinovaných časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="c8666-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="c8666-117">[Postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md) popisuje, jak získat přístup k koordinovaného světového času a místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="c8666-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="c8666-118">[Postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objekt z registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="c8666-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="c8666-119">[Vytvoření instance objektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) popisuje způsoby, ve kterém <xref:System.DateTimeOffset> objekt se dá vytvořit instance a způsoby, ve kterém <xref:System.DateTime> hodnotu lze převést na <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c8666-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="c8666-120">[Postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod do a z letní čas.</span><span class="sxs-lookup"><span data-stu-id="c8666-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="c8666-121">[Postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) popisuje, jak vytvořit vlastní časové pásmo, které podporuje jeden nebo více přechody do a z letní čas.</span><span class="sxs-lookup"><span data-stu-id="c8666-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="c8666-122">[Ukládání a obnova časových pásem](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a ilustruje některého z následujících scénářů, ve kterých se tyto funkce lze použít.</span><span class="sxs-lookup"><span data-stu-id="c8666-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="c8666-123">[Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) popisuje, jak vytvořit vlastní časové pásmo a uložte informace o jeho v souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="c8666-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="c8666-124">[Postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) popisuje, jak vytvořit instanci vlastního časového pásma, které byly uloženy do souboru vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="c8666-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="c8666-125">[Provádění aritmetických operací s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md) popisuje problémy, přidání, odečtením a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c8666-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="c8666-126">[Postupy: používání časových pásem datum a čas aritmetické](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) popisuje, jak provést datum a čas aritmetické odráží pravidla úpravy časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c8666-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="c8666-127">[Převádění mezi DateTime a DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) popisuje, jak pro převod mezi <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c8666-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="c8666-128">[Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md) popisuje, jak převést časy z jednoho časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c8666-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="c8666-129">[Postupy: řešení víceznačných časových údajů](../../../docs/standard/datetime/resolve-ambiguous-times.md) popisuje, jak vyřešit nejednoznačný čas mapování na časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="c8666-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="c8666-130">[Postupy: řešení víceznačných časových údajů uživatelé mohli](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) popisuje, jak může uživatel určit mapování mezi nejednoznačný místní čas a koordinovaného světového času.</span><span class="sxs-lookup"><span data-stu-id="c8666-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="c8666-131">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c8666-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
