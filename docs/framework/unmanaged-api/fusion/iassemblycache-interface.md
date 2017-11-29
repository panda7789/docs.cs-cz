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
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="08f48-102">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="08f48-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="08f48-103">Představuje globální mezipaměti sestavení pro použití technologie fusion.</span><span class="sxs-lookup"><span data-stu-id="08f48-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08f48-104">Metody</span><span class="sxs-lookup"><span data-stu-id="08f48-104">Methods</span></span>  
  
|<span data-ttu-id="08f48-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-105">Method</span></span>|<span data-ttu-id="08f48-106">Popis</span><span class="sxs-lookup"><span data-stu-id="08f48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08f48-107">Createassemblycacheitem – metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="08f48-108">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="08f48-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="08f48-109">Createassemblyscavenger – metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="08f48-110">Technologie fusion vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="08f48-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="08f48-111">Installassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="08f48-112">Nainstaluje zadaný sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="08f48-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="08f48-113">Queryassemblyinfo – metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="08f48-114">Získá požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="08f48-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="08f48-115">Uninstallassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="08f48-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="08f48-116">Odinstaluje zadaný sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="08f48-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08f48-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08f48-117">Requirements</span></span>  
 <span data-ttu-id="08f48-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f48-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f48-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="08f48-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="08f48-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f48-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f48-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="08f48-121">See Also</span></span>  
 [<span data-ttu-id="08f48-122">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="08f48-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="08f48-123">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="08f48-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
