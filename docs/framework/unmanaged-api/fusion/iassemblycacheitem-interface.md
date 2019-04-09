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
ms.openlocfilehash: fba17a2ffad9220acdbc79726efe0d3d4184978a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188549"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="b270f-102">IAssemblyCacheItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b270f-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="b270f-103">Představuje jedno sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b270f-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b270f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b270f-104">Methods</span></span>  
  
|<span data-ttu-id="b270f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b270f-105">Method</span></span>|<span data-ttu-id="b270f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b270f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b270f-107">AbortItem – metoda</span><span class="sxs-lookup"><span data-stu-id="b270f-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="b270f-108">Umožňuje sestavení v globální mezipaměti sestavení před jejich provedl operace čištění.</span><span class="sxs-lookup"><span data-stu-id="b270f-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="b270f-109">Commit – metoda</span><span class="sxs-lookup"><span data-stu-id="b270f-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="b270f-110">Potvrzení odkaz na sestavení v mezipaměti na paměť.</span><span class="sxs-lookup"><span data-stu-id="b270f-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="b270f-111">CreateStream – metoda</span><span class="sxs-lookup"><span data-stu-id="b270f-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="b270f-112">Vytvoří datový proud se zadaným názvem a formát.</span><span class="sxs-lookup"><span data-stu-id="b270f-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b270f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b270f-113">Requirements</span></span>  
 <span data-ttu-id="b270f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b270f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b270f-115">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b270f-115">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="b270f-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b270f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b270f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b270f-117">See also</span></span>

- [<span data-ttu-id="b270f-118">Rozhraní fúze</span><span class="sxs-lookup"><span data-stu-id="b270f-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="b270f-119">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="b270f-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="b270f-120">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b270f-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
