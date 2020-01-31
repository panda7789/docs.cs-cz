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
ms.openlocfilehash: fdd2fee11e9353c3aa3faee2b137597e4ba47801
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791181"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="9ba85-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ba85-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="9ba85-103">Poskytuje oznámení nativních událostí, které přímo nesouvisejí s modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9ba85-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ba85-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9ba85-104">Methods</span></span>  
  
|<span data-ttu-id="9ba85-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ba85-105">Method</span></span>|<span data-ttu-id="9ba85-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9ba85-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ba85-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="9ba85-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="9ba85-108">Oznamuje ladicímu programu, že byla vyvolána nativní událost.</span><span class="sxs-lookup"><span data-stu-id="9ba85-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ba85-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ba85-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ba85-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9ba85-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba85-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ba85-111">Requirements</span></span>  
 <span data-ttu-id="9ba85-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba85-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba85-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9ba85-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ba85-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9ba85-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ba85-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba85-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ba85-116">See also</span></span>

- [<span data-ttu-id="9ba85-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9ba85-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
