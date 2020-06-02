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
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291406"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="b0c0a-102">Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma</span><span class="sxs-lookup"><span data-stu-id="b0c0a-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="b0c0a-103"><xref:System.TimeZoneInfo>Třída poskytuje dvě vlastnosti, <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A> , které přidávají přístup kódu k předdefinovaným objektům časového pásma.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="b0c0a-104">Toto téma popisuje, jak získat přístup k <xref:System.TimeZoneInfo> objektům vráceným těmito vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="b0c0a-105">Přístup k objektu TimeZoneInfo koordinovaného univerzálního času (UTC)</span><span class="sxs-lookup"><span data-stu-id="b0c0a-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="b0c0a-106">`static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Pro přístup k koordinovanému světovému času použijte vlastnost (ve Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b0c0a-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="b0c0a-107">Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je nadále přístup k koordinovanému univerzálnímu času prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="b0c0a-108">Přístup k místnímu časovému pásmu</span><span class="sxs-lookup"><span data-stu-id="b0c0a-108">To access the local time zone</span></span>

1. <span data-ttu-id="b0c0a-109">`static` `Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Pro přístup k časovému pásmu místního systému použijte vlastnost (ve Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b0c0a-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="b0c0a-110">Místo přiřazování <xref:System.TimeZoneInfo> objektu vráceného vlastností proměnné objektu je možné pokračovat v přístupu k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="b0c0a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0c0a-111">Example</span></span>

<span data-ttu-id="b0c0a-112">Následující kód používá <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti a k převodu času z USA a kanadského východního standardního časového pásma a také k zobrazení názvu časového pásma do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="b0c0a-113">Měli byste vždycky přistupovat k místnímu časovému pásmu prostřednictvím <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> vlastnosti místo přiřazení místního časového pásma k <xref:System.TimeZoneInfo> objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b0c0a-114">Podobně byste měli vždycky přistupovat k koordinovanému univerzálnímu času prostřednictvím <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> vlastnosti namísto přiřazení zóny UTC k <xref:System.TimeZoneInfo> objektové proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="b0c0a-115">Tím zabráníte <xref:System.TimeZoneInfo> zrušení platnosti proměnné objektu voláním <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b0c0a-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b0c0a-116">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="b0c0a-116">Compiling the code</span></span>

<span data-ttu-id="b0c0a-117">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b0c0a-117">This example requires:</span></span>

- <span data-ttu-id="b0c0a-118">Tento <xref:System> obor názvů se naimportuje pomocí `using` příkazu (vyžaduje se v kódu jazyka C#).</span><span class="sxs-lookup"><span data-stu-id="b0c0a-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0c0a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0c0a-119">See also</span></span>

- [<span data-ttu-id="b0c0a-120">Data, časy a časová pásma</span><span class="sxs-lookup"><span data-stu-id="b0c0a-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="b0c0a-121">Hledání časových pásem definovaných v lokálním systému</span><span class="sxs-lookup"><span data-stu-id="b0c0a-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="b0c0a-122">Postupy: Vytvoření instance objektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="b0c0a-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
