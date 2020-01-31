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
ms.openlocfilehash: fb6d2e5fc21047fea0928137f983c553f9bb2bbd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867279"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="55890-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="55890-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="55890-103">Ukládá informace o konkrétní instanci klauzule Exception a jejím přidruženém rámci.</span><span class="sxs-lookup"><span data-stu-id="55890-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55890-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55890-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="55890-105">Členové</span><span class="sxs-lookup"><span data-stu-id="55890-105">Members</span></span>  
  
|<span data-ttu-id="55890-106">Člen</span><span class="sxs-lookup"><span data-stu-id="55890-106">Member</span></span>|<span data-ttu-id="55890-107">Popis</span><span class="sxs-lookup"><span data-stu-id="55890-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="55890-108">Hodnota výčtu [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) , která určuje typ klauzule Exception, který kód právě zadal nebo Left.</span><span class="sxs-lookup"><span data-stu-id="55890-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="55890-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah EIP registru x86.</span><span class="sxs-lookup"><span data-stu-id="55890-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="55890-110">Ukazatel na logický rámec pro obslužnou rutinu klauzule, například obsah EBP registru x86.</span><span class="sxs-lookup"><span data-stu-id="55890-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="55890-111">Ukazatel na stínový zásobník.</span><span class="sxs-lookup"><span data-stu-id="55890-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="55890-112">Tato hodnota je obsahem registru BSP a vztahuje se pouze na IA64.</span><span class="sxs-lookup"><span data-stu-id="55890-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55890-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55890-113">Remarks</span></span>  
 <span data-ttu-id="55890-114">Po přijetí oznámení výjimky lze pomocí [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo –](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) získat nativní informace o adrese a snímku pro klauzuli exception (`catch`/`finally`/Filter), která má být spuštěna nebo právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="55890-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="55890-115">Provádění klauzule Exception zahrnuje tato zpětná volání z modulu CLR (Common Language Runtime):</span><span class="sxs-lookup"><span data-stu-id="55890-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="55890-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="55890-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="55890-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="55890-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="55890-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="55890-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="55890-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="55890-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="55890-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="55890-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="55890-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="55890-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="55890-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55890-122">Requirements</span></span>  
 <span data-ttu-id="55890-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55890-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55890-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="55890-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="55890-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="55890-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55890-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55890-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55890-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55890-127">See also</span></span>

- [<span data-ttu-id="55890-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="55890-128">Profiling Structures</span></span>](profiling-structures.md)
