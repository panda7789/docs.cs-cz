---
title: Schéma nastavení spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68f37e3efca784b94be90d5779c9bc402f144448
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530331"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="5bbc5-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="5bbc5-102">Startup Settings Schema</span></span>
<span data-ttu-id="5bbc5-103">Nastavení spuštění zadat verzi common language runtime, který by měla spustit aplikace.</span><span class="sxs-lookup"><span data-stu-id="5bbc5-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="5bbc5-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bbc5-104">Element</span></span>|<span data-ttu-id="5bbc5-105">Popis</span><span class="sxs-lookup"><span data-stu-id="5bbc5-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bbc5-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="5bbc5-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="5bbc5-107">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="5bbc5-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="5bbc5-108">Používejte aplikace sestavené s modulem runtime verze 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="5bbc5-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="5bbc5-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="5bbc5-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="5bbc5-110">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="5bbc5-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="5bbc5-111">\<Po spuštění ></span><span class="sxs-lookup"><span data-stu-id="5bbc5-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="5bbc5-112">Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.</span><span class="sxs-lookup"><span data-stu-id="5bbc5-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bbc5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bbc5-113">See Also</span></span>  
 [<span data-ttu-id="5bbc5-114">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5bbc5-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5bbc5-115">\<PaveOver > Určení verze modulu Runtime, která k použití</span><span class="sxs-lookup"><span data-stu-id="5bbc5-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
