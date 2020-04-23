---
title: Zmírnění nových chování v rozhraní .NET Framework
ms.date: 04/21/2020
ms.openlocfilehash: bd0843ea21a0ff68c6f02b1351f66544dbb200bf
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103539"
---
# <a name="mitigate-new-behaviors-in-net-framework-46-and-later"></a><span data-ttu-id="e5fe6-102">Zmírnění nových chování v rozhraní .NET Framework 4.6 a novějších</span><span class="sxs-lookup"><span data-stu-id="e5fe6-102">Mitigate new behaviors in .NET Framework 4.6 and later</span></span>

<span data-ttu-id="e5fe6-103">Tato část obsahuje články, které popisují skutečnosti snižující závažnost rizika chování, které byly zavedeny v rozhraní .NET Framework 4.6 a novější.</span><span class="sxs-lookup"><span data-stu-id="e5fe6-103">This section contains articles that describe mitigations for behaviors that were introduced in .NET Framework 4.6 and later.</span></span>

<span data-ttu-id="e5fe6-104">Zvažte zmírnění nové chování, pokud způsobuje problémy pro vaši aplikaci nebo je jinak nežádoucí.</span><span class="sxs-lookup"><span data-stu-id="e5fe6-104">Consider mitigating a new behavior if it causes problems for your app or is otherwise undesirable.</span></span> <span data-ttu-id="e5fe6-105">V některých případech můžete také *povolit* nové chování v aplikacích, které cílí na starší verzi rozhraní .NET Framework, ale běží v rozhraní .NET Framework 4.6 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="e5fe6-105">In some cases, you can also *enable* a new behavior on apps that target an older version of .NET Framework but are running on .NET Framework 4.6 or later.</span></span>
