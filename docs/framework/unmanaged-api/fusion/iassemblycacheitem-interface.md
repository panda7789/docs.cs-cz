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
ms.openlocfilehash: 2493b5338824e1eab3f82a9023bbcced59a98fc8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134457"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="7f476-102">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f476-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="7f476-103">Představuje jedno sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="7f476-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f476-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7f476-104">Methods</span></span>  
  
|<span data-ttu-id="7f476-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7f476-105">Method</span></span>|<span data-ttu-id="7f476-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7f476-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f476-107">AbortItem – metoda</span><span class="sxs-lookup"><span data-stu-id="7f476-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="7f476-108">Umožňuje sestavení v globální mezipaměti sestavení provést operace vyčištění před jeho uvolněním.</span><span class="sxs-lookup"><span data-stu-id="7f476-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="7f476-109">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="7f476-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="7f476-110">Potvrdí odkaz na sestavení v mezipaměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="7f476-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="7f476-111">CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="7f476-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="7f476-112">Vytvoří datový proud se zadaným názvem a formátem.</span><span class="sxs-lookup"><span data-stu-id="7f476-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f476-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f476-113">Requirements</span></span>  
 <span data-ttu-id="7f476-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f476-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f476-115">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7f476-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7f476-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f476-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f476-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f476-117">See also</span></span>

- [<span data-ttu-id="7f476-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="7f476-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="7f476-119">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="7f476-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="7f476-120">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f476-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
