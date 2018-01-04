---
title: "Postupy: přístup k místním ČASEM a předdefinované objekty zóny"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="e0096-102">Postupy: přístup k místním ČASEM a předdefinované objekty zóny</span><span class="sxs-lookup"><span data-stu-id="e0096-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="e0096-103"><xref:System.TimeZoneInfo> Třída poskytuje dvě vlastnosti <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, který kód přístup k předdefinovaným objektům časových pásem.</span><span class="sxs-lookup"><span data-stu-id="e0096-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="e0096-104">Toto téma popisuje, jak získat přístup <xref:System.TimeZoneInfo> objektů vrácený tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e0096-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="e0096-105">Pro přístup k objektu TimeZoneInfo koordinovaného světového času (UTC)</span><span class="sxs-lookup"><span data-stu-id="e0096-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="e0096-106">Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost, která koordinovaného světového času.</span><span class="sxs-lookup"><span data-stu-id="e0096-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="e0096-107">Místo přiřazení <xref:System.TimeZoneInfo> objekt byl vrácen vlastností proměnné objektu, i nadále přistupovat k času UTC prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e0096-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="e0096-108">Pro přístup k místním časovém pásmu</span><span class="sxs-lookup"><span data-stu-id="e0096-108">To access the local time zone</span></span>

1. <span data-ttu-id="e0096-109">Použití `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost, která má přístup k časovému pásmu místního systému.</span><span class="sxs-lookup"><span data-stu-id="e0096-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="e0096-110">Místo přiřazení <xref:System.TimeZoneInfo> objekt byl vrácen vlastností proměnné objektu, i nadále přistupovat k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e0096-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="e0096-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0096-111">Example</span></span>

<span data-ttu-id="e0096-112">Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> a <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti pro převod času z USA a Kanadští východní standardní časové pásmo, jakož i zobrazovaný název časového pásma ke konzole.</span><span class="sxs-lookup"><span data-stu-id="e0096-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="e0096-113">By měla vždycky přístup k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnost spíše než přiřazením místního časového pásma na <xref:System.TimeZoneInfo> proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="e0096-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="e0096-114">Podobně, byste měli vždy přistupovat koordinovaný světový čas prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> spíše než přiřazením UTC zóny na <xref:System.TimeZoneInfo> proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="e0096-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="e0096-115">Zabrání se tak <xref:System.TimeZoneInfo> objektová proměnná před zrušením platnosti voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e0096-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e0096-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e0096-116">Compiling the code</span></span>

<span data-ttu-id="e0096-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e0096-117">This example requires:</span></span>

* <span data-ttu-id="e0096-118">Aby byl přidán odkaz na System.Core.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="e0096-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="e0096-119">Zda <xref:System> importovat obor názvů s `using` (povinné v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="e0096-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0096-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0096-120">See also</span></span>

<span data-ttu-id="e0096-121">[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span><span class="sxs-lookup"><span data-stu-id="e0096-121">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span></span>
