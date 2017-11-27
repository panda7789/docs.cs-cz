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
ms.openlocfilehash: 7868fc84ba3003909992334d1a66e1ed243eca18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="1b0f4-102">Icordebugheapvalue – Interface1</span><span class="sxs-lookup"><span data-stu-id="1b0f4-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="1b0f4-103">Podtřídou třídy "ICorDebugValue", který představuje objekt, který se shromáždily systémem common language runtime (CLR) uvolňování.</span><span class="sxs-lookup"><span data-stu-id="1b0f4-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b0f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b0f4-104">Methods</span></span>  
  
|<span data-ttu-id="1b0f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b0f4-105">Method</span></span>|<span data-ttu-id="1b0f4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1b0f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b0f4-107">Createrelocbreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1b0f4-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="1b0f4-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="1b0f4-108">Not implemented.</span></span>|  
|[<span data-ttu-id="1b0f4-109">IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="1b0f4-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="1b0f4-110">Získá hodnotu, která určuje, zda objekt reprezentovaný tímto objektem `ICorDebugHeapValue` je platný, nebo má bylo uvolněno modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="1b0f4-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="1b0f4-111">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="1b0f4-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b0f4-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b0f4-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b0f4-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1b0f4-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b0f4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b0f4-114">Requirements</span></span>  
 <span data-ttu-id="1b0f4-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b0f4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0f4-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b0f4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b0f4-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b0f4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b0f4-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b0f4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0f4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b0f4-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="1b0f4-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b0f4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
