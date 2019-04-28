---
title: ICorProfilerCallback::ExceptionThrown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9cdbc2234519c0dba1a5004246492e7609ea2b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597892"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="2d8bc-102">ICorProfilerCallback::ExceptionThrown – metoda</span><span class="sxs-lookup"><span data-stu-id="2d8bc-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="2d8bc-103">Oznámí profileru, že byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d8bc-104">Tato funkce je volána, pouze v případě, že výjimka dosáhne spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8bc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d8bc-105">Syntax</span></span>  
  
```  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d8bc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d8bc-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="2d8bc-107">[in] ID objektu, která způsobila vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d8bc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d8bc-108">Remarks</span></span>  
 <span data-ttu-id="2d8bc-109">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2d8bc-110">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2d8bc-111">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="2d8bc-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d8bc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d8bc-112">Requirements</span></span>  
 <span data-ttu-id="2d8bc-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d8bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d8bc-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d8bc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d8bc-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d8bc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d8bc-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d8bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8bc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d8bc-117">See also</span></span>

- [<span data-ttu-id="2d8bc-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d8bc-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
