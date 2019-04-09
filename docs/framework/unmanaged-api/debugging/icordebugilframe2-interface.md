---
title: ICorDebugILFrame2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4f57f27ec92e7977b46ebfa5967b0590674d2a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113435"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="9935e-102">ICorDebugILFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9935e-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="9935e-103">Logické rozšíření icordebugilframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9935e-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9935e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9935e-104">Methods</span></span>  
  
|<span data-ttu-id="9935e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9935e-105">Method</span></span>|<span data-ttu-id="9935e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9935e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9935e-107">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="9935e-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="9935e-108">Získá icordebugtypeenum – objekt, který obsahuje <xref:System.Type> parametry v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="9935e-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="9935e-109">RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="9935e-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="9935e-110">Změní funkce se upravila tak, že zadáte nové posun jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="9935e-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9935e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9935e-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9935e-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="9935e-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9935e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9935e-113">Requirements</span></span>  
 <span data-ttu-id="9935e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9935e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9935e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9935e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9935e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9935e-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9935e-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9935e-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9935e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9935e-118">See also</span></span>

- [<span data-ttu-id="9935e-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9935e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
