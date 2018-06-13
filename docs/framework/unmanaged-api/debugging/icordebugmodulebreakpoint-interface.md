---
title: ICorDebugModuleBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c04d5f779306a67e389f768cefdf633f3d72f0ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416134"
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="089e2-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="089e2-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="089e2-103">Poskytuje přístup k určité moduly.</span><span class="sxs-lookup"><span data-stu-id="089e2-103">Provides access to specific modules.</span></span> <span data-ttu-id="089e2-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="089e2-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="089e2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="089e2-105">Methods</span></span>  
  
|<span data-ttu-id="089e2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="089e2-106">Method</span></span>|<span data-ttu-id="089e2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="089e2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="089e2-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="089e2-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="089e2-109">Získá ukazatele rozhraní umožňuje ICorDebugModule, který odkazuje na modul, kde je nastavený tento bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="089e2-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="089e2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="089e2-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="089e2-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="089e2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="089e2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="089e2-112">Requirements</span></span>  
 <span data-ttu-id="089e2-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="089e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089e2-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="089e2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="089e2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="089e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="089e2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089e2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="089e2-117">See Also</span></span>  
 [<span data-ttu-id="089e2-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="089e2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
