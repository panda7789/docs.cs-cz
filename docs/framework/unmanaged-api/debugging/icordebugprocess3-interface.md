---
title: "ICorDebugProcess3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3
helpviewer_keywords: ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8483c53ed8b35fd3948ec42b14859146afa8ce42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="d925a-102">ICorDebugProcess3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d925a-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="d925a-103">Řídí vlastní oznámení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d925a-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d925a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d925a-104">Methods</span></span>  
  
|<span data-ttu-id="d925a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d925a-105">Method</span></span>|<span data-ttu-id="d925a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d925a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d925a-107">Setenablecustomnotification – metoda</span><span class="sxs-lookup"><span data-stu-id="d925a-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="d925a-108">Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="d925a-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d925a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d925a-109">Remarks</span></span>  
 <span data-ttu-id="d925a-110">Toto rozhraní logicky rozšiřuje ICorDebugProcess a icordebugprocess2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d925a-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d925a-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d925a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d925a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d925a-112">Requirements</span></span>  
 <span data-ttu-id="d925a-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d925a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d925a-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d925a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d925a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d925a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d925a-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d925a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d925a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d925a-117">See Also</span></span>  
 [<span data-ttu-id="d925a-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="d925a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d925a-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="d925a-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
