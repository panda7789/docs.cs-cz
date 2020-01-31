---
title: ICorDebugILFrame3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 739c648173d45a9c147ea2a4e469a3a4b518e893
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794339"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="7f9bb-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f9bb-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="7f9bb-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="7f9bb-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="7f9bb-104">`ICorDebugILFrame3` je logické rozšíření rozhraní ICorDebugILFrame a ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="7f9bb-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f9bb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7f9bb-105">Methods</span></span>  
  
|<span data-ttu-id="7f9bb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7f9bb-106">Method</span></span>|<span data-ttu-id="7f9bb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7f9bb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f9bb-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="7f9bb-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="7f9bb-109">Získá objekt ICorDebugValue, který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="7f9bb-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f9bb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f9bb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f9bb-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7f9bb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f9bb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f9bb-112">Requirements</span></span>  
 <span data-ttu-id="7f9bb-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f9bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f9bb-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7f9bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f9bb-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7f9bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f9bb-116">**Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f9bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9bb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f9bb-117">See also</span></span>

- [<span data-ttu-id="7f9bb-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f9bb-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="7f9bb-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7f9bb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
