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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697677"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="11e71-102">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11e71-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="11e71-103">Reprezentuje globální mezipaměti sestavení pro použití technologií fusion.</span><span class="sxs-lookup"><span data-stu-id="11e71-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11e71-104">Metody</span><span class="sxs-lookup"><span data-stu-id="11e71-104">Methods</span></span>  
  
|<span data-ttu-id="11e71-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-105">Method</span></span>|<span data-ttu-id="11e71-106">Popis</span><span class="sxs-lookup"><span data-stu-id="11e71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11e71-107">CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="11e71-108">Získá odkaz na novou [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="11e71-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="11e71-109">CreateAssemblyScavenger – metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="11e71-110">Vyhrazené pro interní použití technologie fusion.</span><span class="sxs-lookup"><span data-stu-id="11e71-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="11e71-111">InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="11e71-112">Nainstaluje zadané sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="11e71-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="11e71-113">QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="11e71-114">Získá požadovaná data o zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="11e71-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="11e71-115">UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="11e71-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="11e71-116">Odinstaluje zadané sestavení z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="11e71-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11e71-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11e71-117">Requirements</span></span>  
 <span data-ttu-id="11e71-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11e71-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e71-119">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="11e71-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="11e71-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e71-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e71-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11e71-121">See also</span></span>

- [<span data-ttu-id="11e71-122">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="11e71-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="11e71-123">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="11e71-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
