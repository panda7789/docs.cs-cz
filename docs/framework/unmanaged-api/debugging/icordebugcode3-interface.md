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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb9aa09447acf28f1ed10ba409ce936cdb4f84a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085035"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="2c676-102">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c676-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="2c676-103">Poskytuje metodu, která rozšiřuje "ICorDebugCode" a "ICorDebugCode2" poskytují informace o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="2c676-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c676-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2c676-104">Methods</span></span>  
  
|<span data-ttu-id="2c676-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2c676-105">Method</span></span>|<span data-ttu-id="2c676-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2c676-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c676-107">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="2c676-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="2c676-108">Pro zadaný posun IL získá nativní posuny, kde by měl být zarážku umístěn tak, aby ladicí program můžete získat návratová hodnota z funkce.</span><span class="sxs-lookup"><span data-stu-id="2c676-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c676-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c676-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c676-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="2c676-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c676-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c676-111">Requirements</span></span>  
 <span data-ttu-id="2c676-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c676-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c676-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c676-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c676-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c676-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c676-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c676-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c676-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c676-116">See also</span></span>

- [<span data-ttu-id="2c676-117">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c676-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="2c676-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2c676-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
