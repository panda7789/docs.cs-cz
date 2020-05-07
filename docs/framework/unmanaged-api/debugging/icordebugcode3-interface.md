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
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893458"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="ca245-102">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca245-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="ca245-103">Poskytuje metodu, která rozšiřuje "ICorDebugCode" a "ICorDebugCode2", aby poskytovala informace o spravované návratové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="ca245-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca245-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca245-104">Methods</span></span>  
  
|<span data-ttu-id="ca245-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca245-105">Method</span></span>|<span data-ttu-id="ca245-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ca245-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca245-107">GetReturnValueLiveOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="ca245-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="ca245-108">U zadaného posunu IL Získá nativní posuny, kde by měla být umístěna zarážka, aby ladicí program mohl získat návratovou hodnotu z funkce.</span><span class="sxs-lookup"><span data-stu-id="ca245-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca245-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca245-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca245-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="ca245-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca245-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca245-111">Requirements</span></span>  
 <span data-ttu-id="ca245-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca245-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca245-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca245-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca245-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ca245-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca245-115">**Verze .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca245-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca245-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca245-116">See also</span></span>

- [<span data-ttu-id="ca245-117">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca245-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="ca245-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca245-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
