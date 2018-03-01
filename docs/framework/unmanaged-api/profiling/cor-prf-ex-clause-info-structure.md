---
title: "COR_PRF_EX_CLAUSE_INFO – struktura"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65025384aa94ac363336bae7f37f8ea88a3bab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="5ec71-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="5ec71-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="5ec71-103">Obsahuje informace o instanci klauzule určité výjimky a jeho přidružené rámečku.</span><span class="sxs-lookup"><span data-stu-id="5ec71-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ec71-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="5ec71-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5ec71-105">Members</span></span>  
  
|<span data-ttu-id="5ec71-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5ec71-106">Member</span></span>|<span data-ttu-id="5ec71-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5ec71-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="5ec71-108">Hodnota [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) výčet, který určuje typ výjimky klauzuli právě zadaný kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="5ec71-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="5ec71-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah X86 EIP registru.</span><span class="sxs-lookup"><span data-stu-id="5ec71-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="5ec71-110">Ukazatel na logické rámce pro obslužnou rutinu klauzule – například obsah X86 EBP registru.</span><span class="sxs-lookup"><span data-stu-id="5ec71-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="5ec71-111">Ukazatel zásobníku stínové.</span><span class="sxs-lookup"><span data-stu-id="5ec71-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="5ec71-112">Tato hodnota je obsah registru BSP a se vztahuje pouze na IA64.</span><span class="sxs-lookup"><span data-stu-id="5ec71-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ec71-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ec71-113">Remarks</span></span>  
 <span data-ttu-id="5ec71-114">Po přijetí oznámení o výjimce [ICorProfilerInfo2::getnotifiedexceptionclauseinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) lze použít k získání nativní adresy a rámce informací pro klauzuli výjimky (`catch` / `finally`/filter), má být spuštěna, nebo byla právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="5ec71-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="5ec71-115">Provádění klauzule výjimka zahrnuje tyto zpětná volání z common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="5ec71-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="5ec71-116">Icorprofilercallback::exceptioncatcherenter –</span><span class="sxs-lookup"><span data-stu-id="5ec71-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="5ec71-117">Icorprofilercallback::exceptionunwindfinallyenter –</span><span class="sxs-lookup"><span data-stu-id="5ec71-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="5ec71-118">Icorprofilercallback::exceptionsearchfilterenter –</span><span class="sxs-lookup"><span data-stu-id="5ec71-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="5ec71-119">Icorprofilercallback::exceptioncatcherleave –</span><span class="sxs-lookup"><span data-stu-id="5ec71-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="5ec71-120">Icorprofilercallback::exceptionunwindfinallyleave –</span><span class="sxs-lookup"><span data-stu-id="5ec71-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="5ec71-121">Icorprofilercallback::exceptionsearchfilterleave –</span><span class="sxs-lookup"><span data-stu-id="5ec71-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="5ec71-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ec71-122">Requirements</span></span>  
 <span data-ttu-id="5ec71-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ec71-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ec71-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5ec71-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5ec71-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ec71-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ec71-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ec71-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec71-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ec71-127">See Also</span></span>  
 [<span data-ttu-id="5ec71-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5ec71-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
