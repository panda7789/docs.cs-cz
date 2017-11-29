---
title: "ICorDebugUnmanagedCallback – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa104bee5171b3b28731cf18a4d26e32f49169ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="e4d7d-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4d7d-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="e4d7d-103">Poskytuje oznámení nativní události, které přímo nesouvisejí s common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e4d7d-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4d7d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4d7d-104">Methods</span></span>  
  
|<span data-ttu-id="e4d7d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4d7d-105">Method</span></span>|<span data-ttu-id="e4d7d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e4d7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4d7d-107">Debugevent – metoda</span><span class="sxs-lookup"><span data-stu-id="e4d7d-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="e4d7d-108">Upozorní ladicí program, že nativní událostí je aktivován.</span><span class="sxs-lookup"><span data-stu-id="e4d7d-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4d7d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4d7d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4d7d-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e4d7d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d7d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4d7d-111">Requirements</span></span>  
 <span data-ttu-id="e4d7d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d7d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d7d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4d7d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4d7d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4d7d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4d7d-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d7d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4d7d-116">See Also</span></span>  
 [<span data-ttu-id="e4d7d-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4d7d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
