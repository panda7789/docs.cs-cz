---
title: "Schéma nastavení spouštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0536197d4cb8b30d99f514d8066e94bf84bffdf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="9759c-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="9759c-102">Startup Settings Schema</span></span>
<span data-ttu-id="9759c-103">Spuštění – nastavení zadejte verzi modulu CLR, která by měla spustit aplikace.</span><span class="sxs-lookup"><span data-stu-id="9759c-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="9759c-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="9759c-104">Element</span></span>|<span data-ttu-id="9759c-105">Popis</span><span class="sxs-lookup"><span data-stu-id="9759c-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9759c-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="9759c-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="9759c-107">Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9759c-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="9759c-108">Aplikace vytvořené s nástroji runtime verze 1.1 by měly používat  **\<supportedRuntime >** element.</span><span class="sxs-lookup"><span data-stu-id="9759c-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="9759c-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="9759c-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="9759c-110">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="9759c-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="9759c-111">\<spuštění ></span><span class="sxs-lookup"><span data-stu-id="9759c-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="9759c-112">Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.</span><span class="sxs-lookup"><span data-stu-id="9759c-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9759c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9759c-113">See Also</span></span>  
 [<span data-ttu-id="9759c-114">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9759c-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9759c-115">\<PaveOver > Zadání kterou verzi modulu Runtime pro použití</span><span class="sxs-lookup"><span data-stu-id="9759c-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
