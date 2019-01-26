---
title: Schéma nastavení spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083415"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="294b7-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="294b7-102">Startup settings schema</span></span>

<span data-ttu-id="294b7-103">Nastavení spuštění zadat verzi common language runtime, který by měla spustit aplikace.</span><span class="sxs-lookup"><span data-stu-id="294b7-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="294b7-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="294b7-104">Element</span></span>|<span data-ttu-id="294b7-105">Popis</span><span class="sxs-lookup"><span data-stu-id="294b7-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="294b7-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="294b7-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="294b7-107">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="294b7-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="294b7-108">Používejte aplikace sestavené s modulem runtime verze 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="294b7-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="294b7-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="294b7-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="294b7-110">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="294b7-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="294b7-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="294b7-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="294b7-112">Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.</span><span class="sxs-lookup"><span data-stu-id="294b7-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="294b7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="294b7-113">See also</span></span>

- [<span data-ttu-id="294b7-114">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="294b7-114">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="294b7-115">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="294b7-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
