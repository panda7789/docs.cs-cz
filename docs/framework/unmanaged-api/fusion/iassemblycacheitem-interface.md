---
title: IAssemblyCacheItem – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c6da86ce2d86a6842d2d7d8de860e9a8621bdaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429592"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="561b9-102">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="561b9-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="561b9-103">Představuje jednoho sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="561b9-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="561b9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="561b9-104">Methods</span></span>  
  
|<span data-ttu-id="561b9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="561b9-105">Method</span></span>|<span data-ttu-id="561b9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="561b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="561b9-107">AbortItem – metoda</span><span class="sxs-lookup"><span data-stu-id="561b9-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="561b9-108">Umožňuje provádět operace čištění před uvolněním sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="561b9-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="561b9-109">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="561b9-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="561b9-110">Potvrdí odkaz na sestavení v mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="561b9-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="561b9-111">CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="561b9-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="561b9-112">Vytvoří datový proud se zadaným názvem a formát.</span><span class="sxs-lookup"><span data-stu-id="561b9-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="561b9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="561b9-113">Requirements</span></span>  
 <span data-ttu-id="561b9-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561b9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561b9-115">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="561b9-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="561b9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561b9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="561b9-117">See Also</span></span>  
 [<span data-ttu-id="561b9-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="561b9-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="561b9-119">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="561b9-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="561b9-120">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="561b9-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
