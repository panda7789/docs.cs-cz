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
ms.openlocfilehash: 61ea6d0c974683e73e835720cff48ff84169217e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="8c82e-102">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="8c82e-102">Startup Settings Schema</span></span>
<span data-ttu-id="8c82e-103">Spuštění – nastavení zadejte verzi modulu CLR, která by měla spustit aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c82e-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="8c82e-104">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c82e-104">Element</span></span>|<span data-ttu-id="8c82e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="8c82e-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c82e-106">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="8c82e-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="8c82e-107">Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="8c82e-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="8c82e-108">Aplikace vytvořené s nástroji runtime verze 1.1 by měly používat  **\<supportedRuntime >** element.</span><span class="sxs-lookup"><span data-stu-id="8c82e-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="8c82e-109">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="8c82e-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="8c82e-110">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="8c82e-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="8c82e-111">\<spuštění ></span><span class="sxs-lookup"><span data-stu-id="8c82e-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="8c82e-112">Obsahuje  **\<requiredRuntime >** a  **\<supportedRuntime >** elementy.</span><span class="sxs-lookup"><span data-stu-id="8c82e-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c82e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c82e-113">See Also</span></span>  
 [<span data-ttu-id="8c82e-114">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8c82e-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="8c82e-115">\<PaveOver > Zadání kterou verzi modulu Runtime pro použití</span><span class="sxs-lookup"><span data-stu-id="8c82e-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
