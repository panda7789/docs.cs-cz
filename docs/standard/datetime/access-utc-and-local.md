---
title: 'Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132609"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="ffae5-102">Postupy: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu</span><span class="sxs-lookup"><span data-stu-id="ffae5-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="ffae5-103">Třída <xref:System.TimeZoneInfo> poskytuje dvě vlastnosti, <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, které poskytují přístup kódu k předdefinovaným objektům časového pásma.</span><span class="sxs-lookup"><span data-stu-id="ffae5-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="ffae5-104">Toto téma popisuje, jak získat přístup k objektům <xref:System.TimeZoneInfo> vráceným těmito vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="ffae5-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="ffae5-105">Přístup k objektu TimeZoneInfo koordinovaného univerzálního času (UTC)</span><span class="sxs-lookup"><span data-stu-id="ffae5-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="ffae5-106">Pro přístup k koordinovanému univerzálnímu času použijte vlastnost <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> `static` (`Shared` in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ffae5-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="ffae5-107">Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je nadále přístup k koordinovanému univerzálnímu času prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="ffae5-108">Přístup k místnímu časovému pásmu</span><span class="sxs-lookup"><span data-stu-id="ffae5-108">To access the local time zone</span></span>

1. <span data-ttu-id="ffae5-109">Pro přístup k časovému pásmu místního systému použijte vlastnost `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="ffae5-110">Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností do proměnné objektu pokračuje v přístupu k místnímu časovému pásmu prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="ffae5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffae5-111">Example</span></span>

<span data-ttu-id="ffae5-112">Následující kód používá vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> k převodu času z USA a kanadského východního standardního časového pásma a také k zobrazení názvu časového pásma pro konzolu.</span><span class="sxs-lookup"><span data-stu-id="ffae5-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="ffae5-113">Měli byste vždycky přistupovat k místnímu časovému pásmu prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> místo přiřazení místního časového pásma k proměnné objektu <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="ffae5-114">Podobně byste měli vždycky přistupovat k koordinovanému univerzálnímu času prostřednictvím vlastnosti <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> místo přiřazení zóny UTC k proměnné objektu <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="ffae5-115">Tím zabráníte zrušení platnosti proměnné objektu <xref:System.TimeZoneInfo> voláním metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffae5-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ffae5-116">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="ffae5-116">Compiling the code</span></span>

<span data-ttu-id="ffae5-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ffae5-117">This example requires:</span></span>

- <span data-ttu-id="ffae5-118">Obor názvů <xref:System> lze importovat pomocí příkazu `using` (požadováno v C# kódu).</span><span class="sxs-lookup"><span data-stu-id="ffae5-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="ffae5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffae5-119">See also</span></span>

- [<span data-ttu-id="ffae5-120">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="ffae5-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="ffae5-121">Hledání časových pásem definovaných v lokálním systému</span><span class="sxs-lookup"><span data-stu-id="ffae5-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="ffae5-122">Postupy: Vytvoření instance objektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="ffae5-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
