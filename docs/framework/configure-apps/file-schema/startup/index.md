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
ms.openlocfilehash: 0a03438968f487f574606f415fb9d43223030038
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222152"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="c6fe3-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="c6fe3-102">Startup settings schema</span></span>

<span data-ttu-id="c6fe3-103">Nastavení spuštění zadat verzi common language runtime, který by měla spustit aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6fe3-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="c6fe3-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6fe3-104">Element</span></span>|<span data-ttu-id="c6fe3-105">Popis</span><span class="sxs-lookup"><span data-stu-id="c6fe3-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6fe3-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="c6fe3-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="c6fe3-107">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c6fe3-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="c6fe3-108">Používejte aplikace sestavené s modulem runtime verze 1.1  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="c6fe3-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="c6fe3-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="c6fe3-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="c6fe3-110">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="c6fe3-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="c6fe3-111">\<Po spuštění ></span><span class="sxs-lookup"><span data-stu-id="c6fe3-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="c6fe3-112">Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.</span><span class="sxs-lookup"><span data-stu-id="c6fe3-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6fe3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6fe3-113">See also</span></span>

- [<span data-ttu-id="c6fe3-114">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c6fe3-114">Configuration File Schema</span></span>](../index.md)  
- [<span data-ttu-id="c6fe3-115">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="c6fe3-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)