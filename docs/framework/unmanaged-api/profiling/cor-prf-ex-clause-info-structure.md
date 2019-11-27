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
ms.openlocfilehash: df4bfe69b22439073342693a03376a0b506f9c70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428370"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="7fe44-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="7fe44-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="7fe44-103">Ukládá informace o konkrétní instanci klauzule Exception a jejím přidruženém rámci.</span><span class="sxs-lookup"><span data-stu-id="7fe44-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fe44-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7fe44-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7fe44-105">Members</span></span>  
  
|<span data-ttu-id="7fe44-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7fe44-106">Member</span></span>|<span data-ttu-id="7fe44-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7fe44-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="7fe44-108">Hodnota výčtu [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) , která určuje typ klauzule Exception, který kód právě zadal nebo Left.</span><span class="sxs-lookup"><span data-stu-id="7fe44-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="7fe44-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah EIP registru x86.</span><span class="sxs-lookup"><span data-stu-id="7fe44-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="7fe44-110">Ukazatel na logický rámec pro obslužnou rutinu klauzule, například obsah EBP registru x86.</span><span class="sxs-lookup"><span data-stu-id="7fe44-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="7fe44-111">Ukazatel na stínový zásobník.</span><span class="sxs-lookup"><span data-stu-id="7fe44-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="7fe44-112">Tato hodnota je obsahem registru BSP a vztahuje se pouze na IA64.</span><span class="sxs-lookup"><span data-stu-id="7fe44-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe44-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fe44-113">Remarks</span></span>  
 <span data-ttu-id="7fe44-114">Po přijetí oznámení výjimky lze pomocí [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) získat nativní informace o adrese a snímku pro klauzuli exception (`catch`/`finally`/Filter), která má být spuštěna nebo právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="7fe44-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="7fe44-115">Provádění klauzule Exception zahrnuje tato zpětná volání z modulu CLR (Common Language Runtime):</span><span class="sxs-lookup"><span data-stu-id="7fe44-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="7fe44-116">ICorProfilerCallback:: ExceptionCatcherEnter –</span><span class="sxs-lookup"><span data-stu-id="7fe44-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="7fe44-117">ICorProfilerCallback:: ExceptionUnwindFinallyEnter –</span><span class="sxs-lookup"><span data-stu-id="7fe44-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="7fe44-118">ICorProfilerCallback:: ExceptionSearchFilterEnter –</span><span class="sxs-lookup"><span data-stu-id="7fe44-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="7fe44-119">ICorProfilerCallback:: ExceptionCatcherLeave –</span><span class="sxs-lookup"><span data-stu-id="7fe44-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="7fe44-120">ICorProfilerCallback:: ExceptionUnwindFinallyLeave –</span><span class="sxs-lookup"><span data-stu-id="7fe44-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="7fe44-121">ICorProfilerCallback:: ExceptionSearchFilterLeave –</span><span class="sxs-lookup"><span data-stu-id="7fe44-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="7fe44-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fe44-122">Requirements</span></span>  
 <span data-ttu-id="7fe44-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fe44-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe44-124">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="7fe44-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7fe44-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7fe44-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fe44-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe44-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe44-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fe44-127">See also</span></span>

- [<span data-ttu-id="7fe44-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7fe44-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
