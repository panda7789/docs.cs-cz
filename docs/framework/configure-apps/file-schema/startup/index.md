---
title: Schéma nastavení spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701512"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="a8c4b-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="a8c4b-102">Startup settings schema</span></span>

<span data-ttu-id="a8c4b-103">Nastavení spuštění určuje verzi modulu CLR (Common Language Runtime), která má aplikaci spustit.</span><span class="sxs-lookup"><span data-stu-id="a8c4b-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="a8c4b-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8c4b-104">Element</span></span>|<span data-ttu-id="a8c4b-105">Description</span><span class="sxs-lookup"><span data-stu-id="a8c4b-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="a8c4b-106">Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a8c4b-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="a8c4b-107">Aplikace sestavené s modulem runtime verze 1,1 by měly používat **\<supportedRuntime>** element.</span><span class="sxs-lookup"><span data-stu-id="a8c4b-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="a8c4b-108">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="a8c4b-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="a8c4b-109">Obsahuje **\<requiredRuntime>** prvky a **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="a8c4b-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8c4b-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8c4b-110">See also</span></span>

- [<span data-ttu-id="a8c4b-111">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a8c4b-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a8c4b-112">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="a8c4b-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
