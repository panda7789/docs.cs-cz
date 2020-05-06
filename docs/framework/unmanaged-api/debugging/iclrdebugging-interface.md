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
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860381"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="b5c9b-102">ICLRDebugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5c9b-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="b5c9b-103">Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b5c9b-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5c9b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b5c9b-104">Methods</span></span>  
  
|<span data-ttu-id="b5c9b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b5c9b-105">Method</span></span>|<span data-ttu-id="b5c9b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b5c9b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5c9b-107">OpenVirtualProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="b5c9b-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="b5c9b-108">Získá rozhraní "ICorDebugProcess", které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.</span><span class="sxs-lookup"><span data-stu-id="b5c9b-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="b5c9b-109">CanUnloadNow – metoda</span><span class="sxs-lookup"><span data-stu-id="b5c9b-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="b5c9b-110">Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b5c9b-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c9b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5c9b-111">Remarks</span></span>  
 <span data-ttu-id="b5c9b-112">Můžete získat instanci `ICLRDebugging` rozhraní pomocí funkce [CLRCreateInstance –](../hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b5c9b-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c9b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5c9b-113">Requirements</span></span>  
 <span data-ttu-id="b5c9b-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c9b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c9b-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5c9b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5c9b-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5c9b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5c9b-117">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c9b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c9b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5c9b-118">See also</span></span>

- [<span data-ttu-id="b5c9b-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5c9b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b5c9b-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="b5c9b-120">Debugging</span></span>](index.md)
