---
title: "Icordebugheapvalue – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue
helpviewer_keywords: ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2ab132b73369526204f8fd811e1567b07b4a9b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="914e3-102">Icordebugheapvalue – Interface1</span><span class="sxs-lookup"><span data-stu-id="914e3-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="914e3-103">Podtřídou třídy "ICorDebugValue", který představuje objekt, který se shromáždily systémem common language runtime (CLR) uvolňování.</span><span class="sxs-lookup"><span data-stu-id="914e3-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="914e3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="914e3-104">Methods</span></span>  
  
|<span data-ttu-id="914e3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="914e3-105">Method</span></span>|<span data-ttu-id="914e3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="914e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="914e3-107">CreateRelocBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="914e3-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="914e3-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="914e3-108">Not implemented.</span></span>|  
|[<span data-ttu-id="914e3-109">IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="914e3-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="914e3-110">Získá hodnotu, která určuje, zda objekt reprezentovaný tímto objektem `ICorDebugHeapValue` je platný, nebo má bylo uvolněno modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="914e3-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="914e3-111">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="914e3-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="914e3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="914e3-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="914e3-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="914e3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914e3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="914e3-114">Requirements</span></span>  
 <span data-ttu-id="914e3-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914e3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914e3-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="914e3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="914e3-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914e3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914e3-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914e3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="914e3-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="914e3-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="914e3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
