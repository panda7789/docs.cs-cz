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
ms.openlocfilehash: 6de440d10f02f177e62ca3d2bd29fd5e98ea9388
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137133"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="93a7f-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93a7f-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="93a7f-103">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="93a7f-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93a7f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93a7f-104">Methods</span></span>  
  
|<span data-ttu-id="93a7f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93a7f-105">Method</span></span>|<span data-ttu-id="93a7f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="93a7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93a7f-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="93a7f-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="93a7f-108">Oznamuje ladicímu programu, že byla vyvolána nativní událost.</span><span class="sxs-lookup"><span data-stu-id="93a7f-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a7f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93a7f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93a7f-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="93a7f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a7f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93a7f-111">Requirements</span></span>  
 <span data-ttu-id="93a7f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a7f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a7f-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93a7f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a7f-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93a7f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a7f-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a7f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93a7f-116">See also</span></span>

- [<span data-ttu-id="93a7f-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="93a7f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
