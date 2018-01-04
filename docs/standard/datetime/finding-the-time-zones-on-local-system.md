---
title: "Hledání časových pásem definovaných v lokálním systému"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e61f05741c1edd86d9baad4f6ebc9f4e91318250
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="6337b-102">Hledání časových pásem definovaných v lokálním systému</span><span class="sxs-lookup"><span data-stu-id="6337b-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="6337b-103"><xref:System.TimeZoneInfo> Třída nevystavuje veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="6337b-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="6337b-104">V důsledku toho `new` – klíčové slovo nelze použít pro vytvoření nového <xref:System.TimeZoneInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="6337b-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="6337b-105">Místo toho <xref:System.TimeZoneInfo> instance objektů načítání informací o předdefinovaných časových pásmech z registru nebo vytváření vlastních časového pásma.</span><span class="sxs-lookup"><span data-stu-id="6337b-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="6337b-106">Toto téma popisuje, vytváření instancí časového pásma z dat uložených v registru.</span><span class="sxs-lookup"><span data-stu-id="6337b-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="6337b-107">Kromě toho `static` (`shared` v jazyce Visual Basic) vlastnosti <xref:System.TimeZoneInfo> třída poskytnout přístup k koordinovaný světový čas (UTC) a místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="6337b-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="6337b-108">Časová pásma, které nejsou definovány v registru, můžete vytvořit vlastní časových pásem voláním přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6337b-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="6337b-109">Vytváření vlastní časové pásmo je popsáno v [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) témata.</span><span class="sxs-lookup"><span data-stu-id="6337b-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="6337b-110">Kromě toho můžete vytvořit instanci <xref:System.TimeZoneInfo> objekt jeho obnovením ze serializované řetězec s <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6337b-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="6337b-111">Serializace a deserializace <xref:System.TimeZoneInfo> objekt je popsán v [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) témata.</span><span class="sxs-lookup"><span data-stu-id="6337b-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="6337b-112">Přístup k jednotlivých časová pásma</span><span class="sxs-lookup"><span data-stu-id="6337b-112">Accessing individual time zones</span></span>

<span data-ttu-id="6337b-113"><xref:System.TimeZoneInfo> Třída poskytuje dva objekty předdefinované časové pásmo, které představují čas UTC a místním časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="6337b-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="6337b-114">Jsou k dispozici z <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A> vlastnosti, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6337b-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="6337b-115">Pokyny pro přístup k UTC nebo místního časového pásma naleznete v tématu [postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="6337b-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="6337b-116">Můžete také vytvořit instanci <xref:System.TimeZoneInfo> objekt, který reprezentuje všechny časové pásmo definované v registru.</span><span class="sxs-lookup"><span data-stu-id="6337b-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="6337b-117">Pokyny týkající se vytváření instance objektu konkrétního časového pásma naleznete v tématu [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="6337b-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="6337b-118">Identifikátory časových pásem</span><span class="sxs-lookup"><span data-stu-id="6337b-118">Time zone identifiers</span></span>

<span data-ttu-id="6337b-119">Identifikátor časového pásma je klíčové pole, která jednoznačně identifikuje časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="6337b-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="6337b-120">Zatímco většina klíče jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho.</span><span class="sxs-lookup"><span data-stu-id="6337b-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="6337b-121">Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> vlastnosti, která slouží k poskytování název časové pásmo (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="6337b-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="6337b-122">Existují však výjimky.</span><span class="sxs-lookup"><span data-stu-id="6337b-122">However, there are exceptions.</span></span> <span data-ttu-id="6337b-123">Vytvoření výčtu časových pásem, který je k dispozici v systému a Všimněte si jejich přidružené identifikátory je nejlepší způsob, jak se ujistěte, že jste zadali platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="6337b-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="6337b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6337b-124">See also</span></span>

<span data-ttu-id="6337b-125">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md)
[postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="6337b-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
