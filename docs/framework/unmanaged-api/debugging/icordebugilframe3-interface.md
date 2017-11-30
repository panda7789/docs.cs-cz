---
title: "ICorDebugILFrame3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame3
api_location: mscordbi.dll
api_type: COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe6affcf82a16a4fd51a5e5a4bf33b247dae0688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="5b006-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b006-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="5b006-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="5b006-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="5b006-104">`ICorDebugILFrame3`je logické rozšíření ICorDebugILFrame a ICorDebugILFrame2 rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b006-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b006-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5b006-105">Methods</span></span>  
  
|<span data-ttu-id="5b006-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b006-106">Method</span></span>|<span data-ttu-id="5b006-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5b006-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b006-108">Getreturnvalueforiloffset – metoda</span><span class="sxs-lookup"><span data-stu-id="5b006-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="5b006-109">Získá objekt ICorDebugValue, který zapouzdří návratovou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="5b006-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b006-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b006-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b006-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5b006-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b006-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b006-112">Requirements</span></span>  
 <span data-ttu-id="5b006-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b006-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b006-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b006-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b006-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b006-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b006-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b006-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b006-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b006-117">See Also</span></span>  
 [<span data-ttu-id="5b006-118">Icordebugcode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b006-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="5b006-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b006-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
