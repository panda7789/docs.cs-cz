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
ms.openlocfilehash: 193604068e379d62107b25f2bc348cd7c8bc6e98
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796708"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="f5fc3-102">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5fc3-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="f5fc3-103">Představuje jedno sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="f5fc3-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5fc3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f5fc3-104">Methods</span></span>  
  
|<span data-ttu-id="f5fc3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5fc3-105">Method</span></span>|<span data-ttu-id="f5fc3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f5fc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5fc3-107">AbortItem – metoda</span><span class="sxs-lookup"><span data-stu-id="f5fc3-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="f5fc3-108">Umožňuje sestavení v globální mezipaměti sestavení provést operace vyčištění před jeho uvolněním.</span><span class="sxs-lookup"><span data-stu-id="f5fc3-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="f5fc3-109">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="f5fc3-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="f5fc3-110">Potvrdí odkaz na sestavení v mezipaměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="f5fc3-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="f5fc3-111">CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="f5fc3-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="f5fc3-112">Vytvoří datový proud se zadaným názvem a formátem.</span><span class="sxs-lookup"><span data-stu-id="f5fc3-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5fc3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5fc3-113">Requirements</span></span>  
 <span data-ttu-id="f5fc3-114">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5fc3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fc3-115">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f5fc3-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f5fc3-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fc3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fc3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5fc3-117">See also</span></span>

- [<span data-ttu-id="f5fc3-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="f5fc3-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="f5fc3-119">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="f5fc3-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="f5fc3-120">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5fc3-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
