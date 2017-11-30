---
title: "ICorProfilerCallback::ExceptionThrown – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionThrown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3986ca8205297a36bb54825a7af72aeb9821f75b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="9b7c7-102">ICorProfilerCallback::ExceptionThrown – metoda</span><span class="sxs-lookup"><span data-stu-id="9b7c7-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="9b7c7-103">Upozorní profileru, že byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b7c7-104">Tato funkce je volána, pouze v případě, že výjimka dosáhne spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7c7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b7c7-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b7c7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b7c7-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="9b7c7-107">[v] ID objektu, který způsobil výjimku, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b7c7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b7c7-108">Remarks</span></span>  
 <span data-ttu-id="9b7c7-109">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9b7c7-110">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9b7c7-111">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9b7c7-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b7c7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b7c7-112">Requirements</span></span>  
 <span data-ttu-id="9b7c7-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b7c7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7c7-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b7c7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b7c7-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b7c7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b7c7-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7c7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7c7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b7c7-117">See Also</span></span>  
 [<span data-ttu-id="9b7c7-118">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b7c7-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
