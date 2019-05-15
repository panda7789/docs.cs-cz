---
title: 'Postupy: Vytváření časových pásem bez pravidel úpravy'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff4cfe2b492b676c061043f018390844f1807440
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586395"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="817aa-102">Postupy: Vytváření časových pásem bez pravidel úpravy</span><span class="sxs-lookup"><span data-stu-id="817aa-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="817aa-103">Informace přesné časové pásmo, který vyžaduje aplikace nemusí být k dispozici na konkrétní systém z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="817aa-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="817aa-104">Časové pásmo je nikdy definována v registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="817aa-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="817aa-105">Data o časovém pásmu, byla změněna nebo odebrána z registru.</span><span class="sxs-lookup"><span data-stu-id="817aa-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="817aa-106">Časové pásmo existuje, ale nemá žádné přesné informace o úpravách časové pásmo pro konkrétní období historické.</span><span class="sxs-lookup"><span data-stu-id="817aa-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="817aa-107">V těchto případech můžete volat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda k definování časové pásmo požadovaná vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="817aa-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="817aa-108">Přetížení této metody můžete použít k vytvoření časové pásmo s nebo bez pravidel úpravy.</span><span class="sxs-lookup"><span data-stu-id="817aa-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="817aa-109">Podporuje-li časové pásmo letního času, můžete definovat úpravy pomocí pravidla buď pevnou nebo plovoucí úpravy.</span><span class="sxs-lookup"><span data-stu-id="817aa-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="817aa-110">(Definice těchto pojmů najdete v části "Časové pásmo terminologie" v [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="817aa-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="817aa-111">Vlastní časové pásmo vytvořených voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda nejsou přidány do registru.</span><span class="sxs-lookup"><span data-stu-id="817aa-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="817aa-112">Místo toho jsou dostupné jenom prostřednictvím odkazu na objekt vrácený <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="817aa-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="817aa-113">Toto téma ukazuje, jak vytvořit časových pásem bez pravidel úpravy.</span><span class="sxs-lookup"><span data-stu-id="817aa-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="817aa-114">Vytvoření časového pásma, které podporuje pravidla úpravy letního času, najdete v tématu [jak: Vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="817aa-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="817aa-115">Chcete-li vytvořit časových pásem bez pravidel úpravy</span><span class="sxs-lookup"><span data-stu-id="817aa-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="817aa-116">Definujte časové pásmo zobrazovaný název.</span><span class="sxs-lookup"><span data-stu-id="817aa-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="817aa-117">Zobrazovaný název následuje poměrně standardní formát, ve kterém časovém pásmu posun od koordinovaného světového času (UTC) není uzavřen v závorkách a následuje řetězec, který určí časové pásmo, jeden nebo více měst v časovém pásmu, nebo v jednom nebo více následujících cou oložky nebo oblasti v časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="817aa-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="817aa-118">Definujte název časového pásma (běžný čas).</span><span class="sxs-lookup"><span data-stu-id="817aa-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="817aa-119">Obvykle tento řetězec se také používá jako identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="817aa-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="817aa-120">Pokud chcete použít jiný identifikátor než název standardního časového pásma, definujte identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="817aa-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="817aa-121">Vytvořit instanci <xref:System.TimeSpan> objekt, který definuje posun časového pásma UTC.</span><span class="sxs-lookup"><span data-stu-id="817aa-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="817aa-122">Časových pásem s časem, které jsou novější než čas UTC mít kladný posun.</span><span class="sxs-lookup"><span data-stu-id="817aa-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="817aa-123">Časových pásem s časem, které jsou starší než čas UTC, mají negativní posun.</span><span class="sxs-lookup"><span data-stu-id="817aa-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="817aa-124">Volání <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metoda pro vytvoření instance nového časového pásma.</span><span class="sxs-lookup"><span data-stu-id="817aa-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="817aa-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="817aa-125">Example</span></span>

<span data-ttu-id="817aa-126">Následující příklad definuje vlastní časové pásmo pro Mawson, základna Antarktida, který nemá žádná pravidla úprav.</span><span class="sxs-lookup"><span data-stu-id="817aa-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="817aa-127">Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnost následuje standardní formát, ve kterém posun časového pásma od UTC Následuje stručný popis časového pásma.</span><span class="sxs-lookup"><span data-stu-id="817aa-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="817aa-128">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="817aa-128">Compiling the code</span></span>

<span data-ttu-id="817aa-129">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="817aa-129">This example requires:</span></span>

* <span data-ttu-id="817aa-130">Aby byly importované následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="817aa-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="817aa-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="817aa-131">See also</span></span>

- [<span data-ttu-id="817aa-132">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="817aa-132">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="817aa-133">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="817aa-133">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="817aa-134">Postupy: Vytváření časových pásem s pravidly úpravy</span><span class="sxs-lookup"><span data-stu-id="817aa-134">How to: Create time zones with adjustment rules</span></span>](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
