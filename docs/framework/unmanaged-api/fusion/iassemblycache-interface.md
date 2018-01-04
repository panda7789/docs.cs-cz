---
title: "IAssemblyCache – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21ebc29a6c442625f7a532f7b1e6a47e7dc4cb69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="6d3cd-102">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d3cd-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="6d3cd-103">Představuje globální mezipaměti sestavení pro použití technologie fusion.</span><span class="sxs-lookup"><span data-stu-id="6d3cd-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d3cd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d3cd-104">Methods</span></span>  
  
|<span data-ttu-id="6d3cd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-105">Method</span></span>|<span data-ttu-id="6d3cd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6d3cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d3cd-107">CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="6d3cd-108">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6d3cd-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="6d3cd-109">CreateAssemblyScavenger – metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="6d3cd-110">Technologie fusion vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="6d3cd-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="6d3cd-111">InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="6d3cd-112">Nainstaluje zadaný sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d3cd-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="6d3cd-113">QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="6d3cd-114">Získá požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d3cd-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="6d3cd-115">UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="6d3cd-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="6d3cd-116">Odinstaluje zadaný sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6d3cd-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d3cd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d3cd-117">Requirements</span></span>  
 <span data-ttu-id="6d3cd-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d3cd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d3cd-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6d3cd-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6d3cd-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d3cd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3cd-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d3cd-121">See Also</span></span>  
 [<span data-ttu-id="6d3cd-122">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="6d3cd-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="6d3cd-123">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="6d3cd-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
