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
ms.openlocfilehash: 5b55b27d45ef3efea10215c8a4163b5981f9d145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422847"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="2918d-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2918d-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="2918d-103">Poskytuje oznámení nativní události, které přímo nesouvisejí s common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2918d-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2918d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2918d-104">Methods</span></span>  
  
|<span data-ttu-id="2918d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2918d-105">Method</span></span>|<span data-ttu-id="2918d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2918d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2918d-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="2918d-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="2918d-108">Upozorní ladicí program, že nativní událostí je aktivován.</span><span class="sxs-lookup"><span data-stu-id="2918d-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2918d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2918d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2918d-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2918d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2918d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2918d-111">Requirements</span></span>  
 <span data-ttu-id="2918d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2918d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2918d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2918d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2918d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2918d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2918d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2918d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2918d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2918d-116">See Also</span></span>  
 [<span data-ttu-id="2918d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2918d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
