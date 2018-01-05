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
ms.workload: dotnet
ms.openlocfilehash: e2a0dc561010ead94f1b2ffcd306a6067a04d7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="36087-102">ICorDebugUnmanagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36087-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="36087-103">Poskytuje oznámení nativní události, které přímo nesouvisejí s common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="36087-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36087-104">Metody</span><span class="sxs-lookup"><span data-stu-id="36087-104">Methods</span></span>  
  
|<span data-ttu-id="36087-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="36087-105">Method</span></span>|<span data-ttu-id="36087-106">Popis</span><span class="sxs-lookup"><span data-stu-id="36087-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36087-107">DebugEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="36087-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="36087-108">Upozorní ladicí program, že nativní událostí je aktivován.</span><span class="sxs-lookup"><span data-stu-id="36087-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36087-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36087-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36087-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="36087-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36087-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36087-111">Requirements</span></span>  
 <span data-ttu-id="36087-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36087-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36087-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36087-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36087-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36087-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36087-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36087-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36087-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="36087-116">See Also</span></span>  
 [<span data-ttu-id="36087-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="36087-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
