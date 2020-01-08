---
title: Průlomové změny – .NET Framework do .NET Core
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 6ec20388e89e59238be3f2d68949059453af216d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443517"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="39e43-103">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="39e43-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="39e43-104">Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="39e43-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="39e43-105">Kromě toho [.NET Framework technologie nedostupné v článku .NET Core](../porting/net-framework-tech-unavailable.md) poskytuje informace o technologiích, které nejsou podporované v .NET Core, například doménách aplikací a vzdálené komunikaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="39e43-105">In addition, the [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md) article provides information about technologies that aren't supported on .NET Core, for example, application domains and .NET remoting.</span></span>

<span data-ttu-id="39e43-106">Zásadní změny jsou seskupené podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="39e43-106">Breaking changes are grouped by category.</span></span>

## <a name="corefx"></a><span data-ttu-id="39e43-107">CoreFx</span><span class="sxs-lookup"><span data-stu-id="39e43-107">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="39e43-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39e43-108">Windows Forms</span></span>

<span data-ttu-id="39e43-109">Informace o tom, jak přenášet změny při migraci model Windows Forms aplikace z .NET Framework na .NET Core 3,0 nebo novější, najdete v tématu [přerušující změny v model Windows Forms (.NET Framework až .NET Core)](../porting/winforms-breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="39e43-109">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39e43-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39e43-110">See also</span></span>

- [<span data-ttu-id="39e43-111">Technologie .NET Framework nedostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="39e43-111">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
