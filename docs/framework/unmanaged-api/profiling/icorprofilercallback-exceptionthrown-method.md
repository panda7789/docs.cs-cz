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
ms.openlocfilehash: 01e407b726ce4426f3b58bc29854b30bd6add257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953880"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="5b799-102">ICorProfilerCallback::ExceptionThrown – metoda</span><span class="sxs-lookup"><span data-stu-id="5b799-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="5b799-103">Upozorní profileru, že byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5b799-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b799-104">Tato funkce je volána pouze v případě, že výjimka dosáhne spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b799-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b799-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b799-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b799-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b799-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="5b799-107">pro ID objektu, který způsobil výjimku vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="5b799-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b799-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b799-108">Remarks</span></span>  
 <span data-ttu-id="5b799-109">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5b799-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5b799-110">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="5b799-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5b799-111">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="5b799-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b799-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b799-112">Requirements</span></span>  
 <span data-ttu-id="5b799-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b799-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b799-114">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b799-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b799-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b799-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b799-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b799-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b799-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b799-117">See also</span></span>

- [<span data-ttu-id="5b799-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b799-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
