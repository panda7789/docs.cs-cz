---
title: ICorDebugUnmanagedCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a34454e7e007b4eba557c712cb824362aa5047c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952978"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="fb3b4-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb3b4-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="fb3b4-103">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="fb3b4-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb3b4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fb3b4-104">Methods</span></span>  
  
|<span data-ttu-id="fb3b4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb3b4-105">Method</span></span>|<span data-ttu-id="fb3b4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fb3b4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb3b4-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="fb3b4-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="fb3b4-108">Oznamuje ladicímu programu, že byla vyvolána nativní událost.</span><span class="sxs-lookup"><span data-stu-id="fb3b4-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3b4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb3b4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb3b4-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fb3b4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb3b4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb3b4-111">Requirements</span></span>  
 <span data-ttu-id="fb3b4-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3b4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3b4-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb3b4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb3b4-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb3b4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb3b4-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3b4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb3b4-116">See also</span></span>

- [<span data-ttu-id="fb3b4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb3b4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
