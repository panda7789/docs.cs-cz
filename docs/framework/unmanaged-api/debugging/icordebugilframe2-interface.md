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
ms.openlocfilehash: c5fa0a67309e23c02393b70d849af3884dfd0adf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788545"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="496dd-102">ICorDebugILFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="496dd-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="496dd-103">Logické rozšíření rozhraní ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="496dd-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="496dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="496dd-104">Methods</span></span>  
  
|<span data-ttu-id="496dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="496dd-105">Method</span></span>|<span data-ttu-id="496dd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="496dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="496dd-107">EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="496dd-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="496dd-108">Získá objekt ICorDebugTypeEnum, který obsahuje parametry <xref:System.Type> v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="496dd-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="496dd-109">RemapFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="496dd-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="496dd-110">Přemapuje upravenou funkci zadáním nového posunu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="496dd-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="496dd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="496dd-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="496dd-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="496dd-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="496dd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="496dd-113">Requirements</span></span>  
 <span data-ttu-id="496dd-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="496dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="496dd-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="496dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="496dd-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="496dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="496dd-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="496dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496dd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="496dd-118">See also</span></span>

- [<span data-ttu-id="496dd-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="496dd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
