---
title: Průlomové změny – .NET Framework do .NET Core
description: Obsahuje seznam přerušujících změn z .NET Framework do .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 5c29636664632e80e4235e922a3296c34fdbef36
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900126"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="8e3f5-103">Zásadní změny migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e3f5-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="8e3f5-104">Pokud migrujete aplikaci z .NET Framework do .NET Core, může to mít vliv na změny, které jsou uvedené v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="8e3f5-105">Zásadní změny jsou seskupené podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-105">Breaking changes are grouped by category.</span></span>

> [!NOTE]
> <span data-ttu-id="8e3f5-106">Tento článek není úplný seznam průlomových změn mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="8e3f5-107">Nejdůležitější nedůležité změny se tady přidají, jak je máme vědět.</span><span class="sxs-lookup"><span data-stu-id="8e3f5-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="8e3f5-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="8e3f5-108">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="8e3f5-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e3f5-109">Windows Forms</span></span>

<span data-ttu-id="8e3f5-110">Informace o tom, jak přenášet změny při migraci model Windows Forms aplikace z .NET Framework na .NET Core 3,0 nebo novější, najdete v tématu [přerušující změny v model Windows Forms (.NET Framework až .NET Core)](../porting/winforms-breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="8e3f5-110">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e3f5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e3f5-111">See also</span></span>

- [<span data-ttu-id="8e3f5-112">Rozhraní API, která vždy vyvolávají výjimky v .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e3f5-112">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="8e3f5-113">Technologie .NET Framework nedostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e3f5-113">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
