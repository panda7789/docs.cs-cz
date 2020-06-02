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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="d9205-102">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="d9205-102">Dates, times, and time zones</span></span>

<span data-ttu-id="d9205-103">Kromě základní <xref:System.DateTime> struktury poskytuje .NET následující třídy, které podporují práci s časovými pásmy:</span><span class="sxs-lookup"><span data-stu-id="d9205-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="d9205-104">Tato třída se používá pro práci s místním časovým pásmem systému a zónou koordinovaného světového času (UTC).</span><span class="sxs-lookup"><span data-stu-id="d9205-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="d9205-105">Funkčnost <xref:System.TimeZone> třídy je převážně nahrazena <xref:System.TimeZoneInfo> třídou.</span><span class="sxs-lookup"><span data-stu-id="d9205-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="d9205-106">Tato třída se používá pro práci s jakýmkoli časovým pásmem, které je předdefinované v systému, k vytváření nových časových pásem a k snadnému převodu dat a časů z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="d9205-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="d9205-107">Pro nový vývoj použijte <xref:System.TimeZoneInfo> třídu namísto <xref:System.TimeZone> třídy.</span><span class="sxs-lookup"><span data-stu-id="d9205-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="d9205-108">Tuto strukturu použijte pro práci s daty a časy, jejichž posun (nebo rozdíl) od času UTC je známý.</span><span class="sxs-lookup"><span data-stu-id="d9205-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="d9205-109"><xref:System.DateTimeOffset>Struktura kombinuje hodnotu data a času s posunem času od času UTC.</span><span class="sxs-lookup"><span data-stu-id="d9205-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="d9205-110">Vzhledem k tomu, že se jedná o vztah ke standardu UTC, hodnota individuálního data a času jednoznačně identifikuje jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="d9205-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="d9205-111">Díky tomu je <xref:System.DateTimeOffset> hodnota lépe přenosná z jednoho počítače na jiný než <xref:System.DateTime> hodnota.</span><span class="sxs-lookup"><span data-stu-id="d9205-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="d9205-112">Tato část dokumentace poskytuje informace, které potřebujete k práci s časovými pásmy a k vytváření aplikací pracujících s časovými pásmy, které mohou převádět data a časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="d9205-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d9205-113">V této části</span><span class="sxs-lookup"><span data-stu-id="d9205-113">In this section</span></span>

<span data-ttu-id="d9205-114">[Přehled časového pásma](time-zone-overview.md) Popisuje terminologii, koncepty a problémy spojené s vytvářením aplikací pracujících s časovými pásmy.</span><span class="sxs-lookup"><span data-stu-id="d9205-114">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="d9205-115">[Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo](choosing-between-datetime.md) Popisuje, kdy použít <xref:System.DateTime> typy, a <xref:System.DateTimeOffset> <xref:System.TimeZoneInfo> při práci s daty data a času.</span><span class="sxs-lookup"><span data-stu-id="d9205-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="d9205-116">[Hledání časových pásem definovaných v místním systému](finding-the-time-zones-on-local-system.md) Popisuje, jak vytvořit výčet časových pásem nalezených v místním systému.</span><span class="sxs-lookup"><span data-stu-id="d9205-116">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="d9205-117">[Postupy: zobrazení výčtu časových pásem v počítači](enumerate-time-zones.md) Poskytuje příklady, které vyčíslují časová pásma definovaná v registru počítače a umožňují uživatelům vybrat předdefinované časové pásmo ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="d9205-117">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="d9205-118">[Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu](access-utc-and-local.md) Popisuje, jak přistupovat k koordinovanému univerzálnímu času a místnímu časovému pásmu.</span><span class="sxs-lookup"><span data-stu-id="d9205-118">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="d9205-119">[Postupy: vytvoření instance objektu TimeZoneInfo](instantiate-time-zone-info.md) Popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objektu z registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="d9205-119">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="d9205-120">[Vytvoření instance objektu DateTimeOffset](instantiating-a-datetimeoffset-object.md) Popisuje způsoby <xref:System.DateTimeOffset> , kterými lze vytvořit instanci objektu, a způsoby, jak <xref:System.DateTime> lze hodnotu převést na <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d9205-120">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="d9205-121">[Postupy: vytváření časových pásem bez pravidel úpravy](create-time-zones-without-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které nepodporuje přechod na a z letního času.</span><span class="sxs-lookup"><span data-stu-id="d9205-121">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="d9205-122">[Postupy: vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md) Popisuje, jak vytvořit vlastní časové pásmo, které podporuje jednu nebo více přechodů do a z letního času.</span><span class="sxs-lookup"><span data-stu-id="d9205-122">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="d9205-123">[Ukládání a obnova časových pásem](saving-and-restoring-time-zones.md) Popisuje <xref:System.TimeZoneInfo> podporu serializace a deserializace dat časového pásma a popisuje některé z scénářů, ve kterých lze tyto funkce použít.</span><span class="sxs-lookup"><span data-stu-id="d9205-123">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="d9205-124">[Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md) Popisuje, jak vytvořit vlastní časové pásmo a uložit jeho informace do souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9205-124">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="d9205-125">[Postupy: Obnovení časových pásem z integrovaného prostředku](restore-time-zones-from-an-embedded-resource.md) Popisuje, jak vytvořit instanci vlastních časových pásem, které byly uloženy do vloženého souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="d9205-125">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="d9205-126">[Provádění aritmetických operací s daty a časy](performing-arithmetic-operations.md) Popisuje problémy, které jsou součástí přidávání, odečítání a porovnávání <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnot.</span><span class="sxs-lookup"><span data-stu-id="d9205-126">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d9205-127">[Postupy: používání časových pásem v aritmetickém datu a čase](use-time-zones-in-arithmetic.md) Popisuje, jak provést aritmetické operace s datem a časem, které odráží pravidla úpravy v časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="d9205-127">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="d9205-128">[Převod mezi DateTime a DateTimeOffset](converting-between-datetime-and-offset.md) Popisuje, jak převést <xref:System.DateTime> hodnoty mezi a <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="d9205-128">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d9205-129">[Převádění časů mezi časovými pásmy](converting-between-time-zones.md) Popisuje, jak převést časy z jednoho časového pásma na jiný.</span><span class="sxs-lookup"><span data-stu-id="d9205-129">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="d9205-130">[Postupy: řešení dvojznačných časů](resolve-ambiguous-times.md) Popisuje, jak vyřešit dvojznačný čas tak, že ho namapujete na standardní čas časového pásma.</span><span class="sxs-lookup"><span data-stu-id="d9205-130">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="d9205-131">[Postupy: převod nejednoznačných časů uživatelů](let-users-resolve-ambiguous-times.md) Popisuje, jak umožnit uživateli určit mapování mezi nejednoznačným místním časem a koordinovaným světovým časem.</span><span class="sxs-lookup"><span data-stu-id="d9205-131">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="d9205-132">Reference</span><span class="sxs-lookup"><span data-stu-id="d9205-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
