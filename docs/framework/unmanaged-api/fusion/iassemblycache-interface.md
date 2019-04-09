---
title: IAssemblyCache – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fc5f3a3d5bc5699a596bcc648a7153190c130f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075628"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="754e8-102">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="754e8-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="754e8-103">Reprezentuje globální mezipaměti sestavení pro použití technologií fusion.</span><span class="sxs-lookup"><span data-stu-id="754e8-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="754e8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="754e8-104">Methods</span></span>  
  
|<span data-ttu-id="754e8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-105">Method</span></span>|<span data-ttu-id="754e8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="754e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="754e8-107">CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="754e8-108">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="754e8-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="754e8-109">CreateAssemblyScavenger – metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="754e8-110">Vyhrazené pro interní použití technologie fusion.</span><span class="sxs-lookup"><span data-stu-id="754e8-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="754e8-111">InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="754e8-112">Nainstaluje zadané sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="754e8-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="754e8-113">QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="754e8-114">Získá požadovaná data o zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="754e8-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="754e8-115">UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="754e8-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="754e8-116">Odinstaluje zadané sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="754e8-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="754e8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="754e8-117">Requirements</span></span>  
 <span data-ttu-id="754e8-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="754e8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="754e8-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="754e8-119">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="754e8-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="754e8-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="754e8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="754e8-121">See also</span></span>

- [<span data-ttu-id="754e8-122">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="754e8-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="754e8-123">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="754e8-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
