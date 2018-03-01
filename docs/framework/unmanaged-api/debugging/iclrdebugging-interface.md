---
title: "ICLRDebugging – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 325f6adf8fe3a357f903f0cb047a2255ef80e264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="bad6c-102">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bad6c-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="bad6c-103">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="bad6c-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bad6c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bad6c-104">Methods</span></span>  
  
|<span data-ttu-id="bad6c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bad6c-105">Method</span></span>|<span data-ttu-id="bad6c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bad6c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bad6c-107">OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="bad6c-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="bad6c-108">Získá rozhraní "ICorDebugProcess", která odpovídá common language runtime (CLR) modul načíst v procesu.</span><span class="sxs-lookup"><span data-stu-id="bad6c-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="bad6c-109">CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="bad6c-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="bad6c-110">Určuje, zda knihovnu, která byla vydána v [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní je stále používáno nebo může být odpojen.</span><span class="sxs-lookup"><span data-stu-id="bad6c-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad6c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bad6c-111">Remarks</span></span>  
 <span data-ttu-id="bad6c-112">Můžete získat instanci `ICLRDebugging` rozhraní pomocí [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="bad6c-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad6c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bad6c-113">Requirements</span></span>  
 <span data-ttu-id="bad6c-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad6c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad6c-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bad6c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bad6c-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bad6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bad6c-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad6c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="bad6c-118">See Also</span></span>  
 [<span data-ttu-id="bad6c-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bad6c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bad6c-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="bad6c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
