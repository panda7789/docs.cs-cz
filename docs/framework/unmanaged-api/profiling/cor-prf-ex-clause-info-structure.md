---
title: COR_PRF_EX_CLAUSE_INFO – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85c0cc3880e4fc78d4badea329d62a6fced2a977
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781947"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="2f7d9-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="2f7d9-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="2f7d9-103">Ukládá informace o instanci klauzule specifickou výjimku a jeho přidružené rámce.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f7d9-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2f7d9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2f7d9-105">Members</span></span>  
  
|<span data-ttu-id="2f7d9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2f7d9-106">Member</span></span>|<span data-ttu-id="2f7d9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7d9-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="2f7d9-108">Hodnota [cor_prf_clause_type –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) výčet, který určuje typ výjimky klauzule kód zadali nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="2f7d9-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah X86 EIP registru.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="2f7d9-110">Ukazatel na logický rámec pro obslužnou rutinu klauzule – například obsah X86 EBP registru.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="2f7d9-111">Ukazatel na stínového zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="2f7d9-112">Tato hodnota je obsah registru BSP a platí jenom pro IA64.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f7d9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f7d9-113">Remarks</span></span>  
 <span data-ttu-id="2f7d9-114">Po přijetí oznámení o výjimce [ICorProfilerInfo2::getnotifiedexceptionclauseinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) můžete použít k získání nativní rámce informace o adrese a pro klauzuli výjimky (`catch` / `finally`/filtrování), který má být spuštěna, nebo jenom nebyly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="2f7d9-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="2f7d9-115">Spuštění klauzule výjimka zahrnuje tato zpětná volání z common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="2f7d9-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="2f7d9-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="2f7d9-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="2f7d9-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="2f7d9-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="2f7d9-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="2f7d9-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="2f7d9-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="2f7d9-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="2f7d9-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="2f7d9-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="2f7d9-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="2f7d9-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="2f7d9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f7d9-122">Requirements</span></span>  
 <span data-ttu-id="2f7d9-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f7d9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f7d9-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2f7d9-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2f7d9-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f7d9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f7d9-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f7d9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7d9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f7d9-127">See also</span></span>

- [<span data-ttu-id="2f7d9-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2f7d9-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
