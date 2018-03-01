---
title: "ICorDebugMDA – rozhraní"
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
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c53e03acddc5d732a684cf825bce49a65bb4c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="aeaa0-102">ICorDebugMDA – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aeaa0-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="aeaa0-103">Představuje zprávu pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeaa0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aeaa0-104">Methods</span></span>  
  
|<span data-ttu-id="aeaa0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-105">Method</span></span>|<span data-ttu-id="aeaa0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="aeaa0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeaa0-107">GetDescription – metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="aeaa0-108">Získá řetězec, který obsahuje popis této (mda).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="aeaa0-109">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="aeaa0-110">Získá příznaky přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="aeaa0-111">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="aeaa0-112">Získá řetězec, který obsahuje název této (mda).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="aeaa0-113">GetOSThreadId – metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="aeaa0-114">Získá identifikátor operačního systému přístup z více vláken, na kterém je tento MDA provádění.</span><span class="sxs-lookup"><span data-stu-id="aeaa0-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="aeaa0-115">GetXML – metoda</span><span class="sxs-lookup"><span data-stu-id="aeaa0-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="aeaa0-116">Získá úplný datový proud XML přidružené k této (mda).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeaa0-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aeaa0-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeaa0-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="aeaa0-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeaa0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aeaa0-119">Requirements</span></span>  
 <span data-ttu-id="aeaa0-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeaa0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeaa0-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeaa0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeaa0-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeaa0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeaa0-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeaa0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaa0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="aeaa0-124">See Also</span></span>  
 [<span data-ttu-id="aeaa0-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aeaa0-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="aeaa0-126">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="aeaa0-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
