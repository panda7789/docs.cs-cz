---
title: ICorDebugCode4 Interface
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c38ce53ca1c02ead03ab9d1ff1e53cda772333f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739716"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="6e741-102">ICorDebugCode4 Interface</span><span class="sxs-lookup"><span data-stu-id="6e741-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="6e741-103">Poskytuje metodu, která umožňuje ladicí program, který výčet lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="6e741-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e741-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6e741-104">Methods</span></span>  
  
|<span data-ttu-id="6e741-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e741-105">Method</span></span>|<span data-ttu-id="6e741-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6e741-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e741-107">EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="6e741-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="6e741-108">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="6e741-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e741-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e741-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e741-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="6e741-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e741-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e741-111">Requirements</span></span>  
 <span data-ttu-id="6e741-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e741-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e741-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e741-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e741-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e741-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e741-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e741-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e741-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e741-116">See also</span></span>


- [<span data-ttu-id="6e741-117">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e741-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="6e741-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6e741-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
