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
ms.openlocfilehash: d02dab01eca3bd4f8ce3ae7ace7f9d4be8233dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917006"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="8b870-102">ICorDebugILFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b870-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="8b870-103">Logické rozšíření rozhraní ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="8b870-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b870-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b870-104">Methods</span></span>  
  
|<span data-ttu-id="8b870-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b870-105">Method</span></span>|<span data-ttu-id="8b870-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8b870-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b870-107">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="8b870-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="8b870-108">Získá objekt ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="8b870-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="8b870-109">RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="8b870-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="8b870-110">Přemapuje upravenou funkci zadáním nového posunu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="8b870-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b870-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b870-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b870-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8b870-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b870-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b870-113">Requirements</span></span>  
 <span data-ttu-id="8b870-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b870-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b870-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b870-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b870-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b870-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b870-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b870-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b870-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b870-118">See also</span></span>

- [<span data-ttu-id="8b870-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8b870-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
