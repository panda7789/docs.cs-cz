---
title: ICorDebugCode3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777816"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="6167c-102">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6167c-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="6167c-103">Poskytuje metodu, která rozšiřuje "ICorDebugCode" a "ICorDebugCode2", aby poskytovala informace o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="6167c-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6167c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6167c-104">Methods</span></span>  
  
|<span data-ttu-id="6167c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6167c-105">Method</span></span>|<span data-ttu-id="6167c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6167c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6167c-107">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="6167c-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="6167c-108">U zadaného posunu IL Získá nativní posuny, kde by měla být umístěna zarážka, aby ladicí program mohl získat návratovou hodnotu z funkce.</span><span class="sxs-lookup"><span data-stu-id="6167c-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6167c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6167c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6167c-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6167c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6167c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6167c-111">Requirements</span></span>  
 <span data-ttu-id="6167c-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6167c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6167c-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6167c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6167c-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6167c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6167c-115">**Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6167c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6167c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6167c-116">See also</span></span>

- [<span data-ttu-id="6167c-117">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6167c-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="6167c-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6167c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
