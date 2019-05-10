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
ms.openlocfilehash: 148ca261e717b9a54192a13c317fe385b98f4ccd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651166"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="1bd5f-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="1bd5f-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="1bd5f-103">Ukládá informace o instanci klauzule specifickou výjimku a jeho přidružené rámce.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd5f-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1bd5f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1bd5f-105">Members</span></span>  
  
|<span data-ttu-id="1bd5f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1bd5f-106">Member</span></span>|<span data-ttu-id="1bd5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1bd5f-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="1bd5f-108">Hodnota [cor_prf_clause_type –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) výčet, který určuje typ výjimky klauzule kód zadali nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="1bd5f-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah X86 EIP registru.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="1bd5f-110">Ukazatel na logický rámec pro obslužnou rutinu klauzule – například obsah X86 EBP registru.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="1bd5f-111">Ukazatel na stínového zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="1bd5f-112">Tato hodnota je obsah registru BSP a platí jenom pro IA64.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd5f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bd5f-113">Remarks</span></span>  
 <span data-ttu-id="1bd5f-114">Po přijetí oznámení o výjimce [ICorProfilerInfo2::getnotifiedexceptionclauseinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) můžete použít k získání nativní rámce informace o adrese a pro klauzuli výjimky (`catch` / `finally`/filtrování), který má být spuštěna, nebo jenom nebyly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="1bd5f-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="1bd5f-115">Spuštění klauzule výjimka zahrnuje tato zpětná volání z common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="1bd5f-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="1bd5f-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="1bd5f-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="1bd5f-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="1bd5f-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="1bd5f-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="1bd5f-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="1bd5f-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="1bd5f-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="1bd5f-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="1bd5f-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="1bd5f-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="1bd5f-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="1bd5f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bd5f-122">Requirements</span></span>  
 <span data-ttu-id="1bd5f-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd5f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd5f-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1bd5f-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1bd5f-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd5f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd5f-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd5f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd5f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bd5f-127">See also</span></span>

- [<span data-ttu-id="1bd5f-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1bd5f-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
