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
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278035"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="5760b-102">Postupy: Vytváření časových pásem bez pravidel úpravy</span><span class="sxs-lookup"><span data-stu-id="5760b-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="5760b-103">Přesné informace o časovém pásmu, které vyžaduje aplikace, nemusí být k dispozici v konkrétním systému z několika důvodů:</span><span class="sxs-lookup"><span data-stu-id="5760b-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="5760b-104">Časové pásmo nebylo nikdy definováno v registru místního systému.</span><span class="sxs-lookup"><span data-stu-id="5760b-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="5760b-105">Data o časovém pásmu byla upravena nebo odebrána z registru.</span><span class="sxs-lookup"><span data-stu-id="5760b-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="5760b-106">Časové pásmo existuje, ale nemá přesné informace o úpravách časového pásma pro konkrétní historické období.</span><span class="sxs-lookup"><span data-stu-id="5760b-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="5760b-107">V těchto případech můžete zavolat <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodu pro definování časového pásma vyžadovaného vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="5760b-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="5760b-108">Pomocí přetížení této metody můžete vytvořit časové pásmo s pravidly úprav nebo bez nich.</span><span class="sxs-lookup"><span data-stu-id="5760b-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="5760b-109">Pokud časové pásmo podporuje letní čas, můžete definovat úpravy s pravidly úpravy s pevnou nebo plovoucí.</span><span class="sxs-lookup"><span data-stu-id="5760b-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="5760b-110">(Pro definice těchto podmínek si přečtěte část "Terminologie časových pásem" v tématu [Přehled časového pásma](time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="5760b-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5760b-111">Vlastní časová pásma vytvořená voláním <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nejsou přidána do registru.</span><span class="sxs-lookup"><span data-stu-id="5760b-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="5760b-112">Místo toho mohou být k dispozici pouze prostřednictvím odkazu objektu vráceného <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="5760b-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="5760b-113">V tomto tématu se dozvíte, jak vytvořit časové pásmo bez pravidel úprav.</span><span class="sxs-lookup"><span data-stu-id="5760b-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="5760b-114">Chcete-li vytvořit časové pásmo, které podporuje pravidla úprav letního času, přečtěte si téma [Postup: vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="5760b-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="5760b-115">Vytvoření časového pásma bez pravidel úpravy</span><span class="sxs-lookup"><span data-stu-id="5760b-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="5760b-116">Zadejte zobrazovaný název časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="5760b-117">Zobrazovaný název se řídí poměrně standardním formátem, ve kterém je posun časového pásma od koordinovaného světového času (UTC) uzavřený v závorkách a následován řetězcem, který určuje časové pásmo, jednu nebo více měst v časovém pásmu nebo jednu nebo více zemí nebo oblastí v časovém pásmu.</span><span class="sxs-lookup"><span data-stu-id="5760b-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="5760b-118">Zadejte název standardního času časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="5760b-119">Obvykle se tento řetězec používá také jako identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="5760b-120">Pokud chcete použít jiný identifikátor než standardní název časového pásma, definujte identifikátor časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="5760b-121">Vytvořte instanci <xref:System.TimeSpan> objektu, který definuje posun časového pásma od času UTC.</span><span class="sxs-lookup"><span data-stu-id="5760b-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="5760b-122">Časová pásma s časy, které jsou pozdější než UTC, mají kladný posun.</span><span class="sxs-lookup"><span data-stu-id="5760b-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="5760b-123">Časová pásma s časy, které jsou starší než UTC, mají záporný posun.</span><span class="sxs-lookup"><span data-stu-id="5760b-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="5760b-124">Zavolejte <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metodu pro vytvoření instance nového časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="5760b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5760b-125">Example</span></span>

<span data-ttu-id="5760b-126">Následující příklad definuje vlastní časové pásmo pro Mawson, Antarktida, které nemá žádná pravidla úprav.</span><span class="sxs-lookup"><span data-stu-id="5760b-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="5760b-127">Řetězec přiřazený k <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti následuje po standardním formátu, ve kterém je posun časového pásma od času UTC následován popisným popisem časového pásma.</span><span class="sxs-lookup"><span data-stu-id="5760b-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="5760b-128">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="5760b-128">Compiling the code</span></span>

<span data-ttu-id="5760b-129">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5760b-129">This example requires:</span></span>

- <span data-ttu-id="5760b-130">Následující obory názvů se naimportují:</span><span class="sxs-lookup"><span data-stu-id="5760b-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="5760b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5760b-131">See also</span></span>

- [<span data-ttu-id="5760b-132">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="5760b-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="5760b-133">Přehled časových pásem</span><span class="sxs-lookup"><span data-stu-id="5760b-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="5760b-134">Postupy: Vytváření časových pásem s pravidly úpravy</span><span class="sxs-lookup"><span data-stu-id="5760b-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
