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
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796780"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="c0def-102">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0def-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="c0def-103">Představuje globální mezipaměť sestavení pro použití technologií Fusion.</span><span class="sxs-lookup"><span data-stu-id="c0def-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0def-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c0def-104">Methods</span></span>  
  
|<span data-ttu-id="c0def-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-105">Method</span></span>|<span data-ttu-id="c0def-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c0def-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0def-107">CreateAssemblyCacheItem – metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="c0def-108">Získá odkaz na nový [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c0def-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="c0def-109">CreateAssemblyScavenger – metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="c0def-110">Vyhrazeno pro interní použití technologií Fusion.</span><span class="sxs-lookup"><span data-stu-id="c0def-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="c0def-111">InstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="c0def-112">Nainstaluje zadané sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="c0def-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="c0def-113">QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="c0def-114">Načte požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="c0def-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="c0def-115">UninstallAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="c0def-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="c0def-116">Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="c0def-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0def-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0def-117">Requirements</span></span>  
 <span data-ttu-id="c0def-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0def-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0def-119">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c0def-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c0def-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0def-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0def-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0def-121">See also</span></span>

- [<span data-ttu-id="c0def-122">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="c0def-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="c0def-123">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="c0def-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)
