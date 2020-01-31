---
title: ICLRDebugging – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793630"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="b4083-102">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4083-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="b4083-103">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b4083-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4083-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b4083-104">Methods</span></span>  
  
|<span data-ttu-id="b4083-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4083-105">Method</span></span>|<span data-ttu-id="b4083-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b4083-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4083-107">OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="b4083-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="b4083-108">Získá rozhraní "ICorDebugProcess", které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.</span><span class="sxs-lookup"><span data-stu-id="b4083-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="b4083-109">CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="b4083-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="b4083-110">Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b4083-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4083-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4083-111">Remarks</span></span>  
 <span data-ttu-id="b4083-112">Můžete získat instanci rozhraní `ICLRDebugging` pomocí funkce [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b4083-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4083-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4083-113">Requirements</span></span>  
 <span data-ttu-id="b4083-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4083-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4083-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4083-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4083-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4083-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4083-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4083-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4083-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4083-118">See also</span></span>

- [<span data-ttu-id="b4083-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4083-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b4083-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="b4083-120">Debugging</span></span>](index.md)
