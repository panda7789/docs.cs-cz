---
title: 'Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586426"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="c0623-102">Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma</span><span class="sxs-lookup"><span data-stu-id="c0623-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="c0623-103"><xref:System.TimeZoneInfo> Třída poskytuje dvě vlastnosti <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, který kód přístup k předdefinované objekty časového pásma.</span><span class="sxs-lookup"><span data-stu-id="c0623-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="c0623-104">Toto téma popisuje, jak získat přístup k <xref:System.TimeZoneInfo> objektů vrácených podle vlastností.</span><span class="sxs-lookup"><span data-stu-id="c0623-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="c0623-105">Pro přístup k objektu TimeZoneInfo koordinovaný univerzální čas (UTC)</span><span class="sxs-lookup"><span data-stu-id="c0623-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="c0623-106">Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro přístup k koordinovaný světový čas.</span><span class="sxs-lookup"><span data-stu-id="c0623-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="c0623-107">Místo toho <xref:System.TimeZoneInfo> objekt vráceného vlastností do proměnné objektu, dál přístup k koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c0623-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="c0623-108">Pro přístup k místním časovém pásmu</span><span class="sxs-lookup"><span data-stu-id="c0623-108">To access the local time zone</span></span>

1. <span data-ttu-id="c0623-109">Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti přístupu k časovému pásmu místního systému.</span><span class="sxs-lookup"><span data-stu-id="c0623-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="c0623-110">Místo toho <xref:System.TimeZoneInfo> objekt vráceného vlastností do proměnné objektu, dál přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c0623-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="c0623-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0623-111">Example</span></span>

<span data-ttu-id="c0623-112">Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro převod z USA a Kanadské standardní východní časové pásmo času, jakož i zobrazovaný název časového pásma do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c0623-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="c0623-113">By měla vždycky přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost spíše než přiřazením místního časového pásma na <xref:System.TimeZoneInfo> proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="c0623-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="c0623-114">Podobně by měla vždycky přístup koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> spíše než přiřazením čas UTC pásma <xref:System.TimeZoneInfo> proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="c0623-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="c0623-115">Díky tomu <xref:System.TimeZoneInfo> proměnné objektu před zrušením platnosti voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="c0623-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c0623-116">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="c0623-116">Compiling the code</span></span>

<span data-ttu-id="c0623-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c0623-117">This example requires:</span></span>

* <span data-ttu-id="c0623-118">Že <xref:System> obor názvů je importovat s `using` – příkaz (vyžadováno za kód jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="c0623-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0623-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0623-119">See also</span></span>

- [<span data-ttu-id="c0623-120">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="c0623-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="c0623-121">Hledání časových pásem definovaných v lokálním systému</span><span class="sxs-lookup"><span data-stu-id="c0623-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="c0623-122">Postupy: Vytvoření instance objektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="c0623-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
