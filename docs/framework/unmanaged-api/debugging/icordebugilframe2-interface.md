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
ms.openlocfilehash: 08c2946a9bd6251f377ea594c0c3ca5d1bd98c67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095095"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="24209-102">ICorDebugILFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24209-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="24209-103">Logické rozšíření rozhraní ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="24209-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24209-104">Metody</span><span class="sxs-lookup"><span data-stu-id="24209-104">Methods</span></span>  
  
|<span data-ttu-id="24209-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="24209-105">Method</span></span>|<span data-ttu-id="24209-106">Popis</span><span class="sxs-lookup"><span data-stu-id="24209-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24209-107">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="24209-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="24209-108">Získá objekt ICorDebugTypeEnum, který obsahuje parametry <xref:System.Type> v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="24209-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="24209-109">RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="24209-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="24209-110">Přemapuje upravenou funkci zadáním nového posunu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="24209-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24209-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24209-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24209-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="24209-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24209-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24209-113">Requirements</span></span>  
 <span data-ttu-id="24209-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24209-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24209-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="24209-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24209-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="24209-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24209-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24209-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24209-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24209-118">See also</span></span>

- [<span data-ttu-id="24209-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="24209-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
