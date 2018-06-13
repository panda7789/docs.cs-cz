---
title: ICorDebugCode4 rozhraní
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
ms.openlocfilehash: 624db77f0db2fe374e16abae64b6bf6ad290baa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411431"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="20308-102">ICorDebugCode4 rozhraní</span><span class="sxs-lookup"><span data-stu-id="20308-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="20308-103">Poskytne metodu, která umožňuje ladicí program výčet místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="20308-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20308-104">Metody</span><span class="sxs-lookup"><span data-stu-id="20308-104">Methods</span></span>  
  
|<span data-ttu-id="20308-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="20308-105">Method</span></span>|<span data-ttu-id="20308-106">Popis</span><span class="sxs-lookup"><span data-stu-id="20308-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20308-107">EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="20308-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="20308-108">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="20308-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20308-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20308-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20308-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="20308-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20308-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20308-111">Requirements</span></span>  
 <span data-ttu-id="20308-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20308-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20308-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20308-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20308-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20308-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20308-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20308-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20308-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="20308-116">See Also</span></span>  
    
    
 [<span data-ttu-id="20308-117">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20308-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="20308-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="20308-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
