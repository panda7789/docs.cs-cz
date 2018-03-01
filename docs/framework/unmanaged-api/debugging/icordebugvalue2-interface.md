---
title: "ICorDebugValue2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7611bfa0c06bc254a720ce9bc39935aa209d52e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="67ce0-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67ce0-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="67ce0-103">Rozšiřuje rozhraní "ICorDebugValue" poskytovat podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="67ce0-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67ce0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="67ce0-104">Methods</span></span>  
  
|<span data-ttu-id="67ce0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="67ce0-105">Method</span></span>|<span data-ttu-id="67ce0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="67ce0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67ce0-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="67ce0-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="67ce0-108">Získá ukazatele rozhraní k `ICorDebugType` objekt, který reprezentuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67ce0-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ce0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67ce0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ce0-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="67ce0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ce0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67ce0-111">Requirements</span></span>  
 <span data-ttu-id="67ce0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ce0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ce0-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67ce0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ce0-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ce0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ce0-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ce0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ce0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="67ce0-116">See Also</span></span>  
 [<span data-ttu-id="67ce0-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="67ce0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
    
 [<span data-ttu-id="67ce0-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67ce0-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
