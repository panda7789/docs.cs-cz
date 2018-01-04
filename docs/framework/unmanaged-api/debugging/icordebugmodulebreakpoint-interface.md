---
title: ICorDebugModuleBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cec51a7efe17c2188f12039333dd90f557b1e724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="6a5df-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="6a5df-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="6a5df-103">Poskytuje přístup k určité moduly.</span><span class="sxs-lookup"><span data-stu-id="6a5df-103">Provides access to specific modules.</span></span> <span data-ttu-id="6a5df-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="6a5df-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a5df-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6a5df-105">Methods</span></span>  
  
|<span data-ttu-id="6a5df-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a5df-106">Method</span></span>|<span data-ttu-id="6a5df-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6a5df-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a5df-108">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="6a5df-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="6a5df-109">Získá ukazatele rozhraní umožňuje ICorDebugModule, který odkazuje na modul, kde je nastavený tento bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="6a5df-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a5df-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a5df-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a5df-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6a5df-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a5df-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a5df-112">Requirements</span></span>  
 <span data-ttu-id="6a5df-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5df-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5df-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a5df-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a5df-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a5df-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a5df-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5df-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a5df-117">See Also</span></span>  
 [<span data-ttu-id="6a5df-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6a5df-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
