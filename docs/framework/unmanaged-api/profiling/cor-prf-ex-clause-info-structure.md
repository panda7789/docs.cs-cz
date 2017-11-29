---
title: "COR_PRF_EX_CLAUSE_INFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_EX_CLAUSE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords: COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9952ea1d8c806c9d3ac5357d933092fb82351484
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="66bcf-102">COR_PRF_EX_CLAUSE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="66bcf-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="66bcf-103">Obsahuje informace o instanci klauzule určité výjimky a jeho přidružené rámečku.</span><span class="sxs-lookup"><span data-stu-id="66bcf-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66bcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66bcf-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="66bcf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="66bcf-105">Members</span></span>  
  
|<span data-ttu-id="66bcf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="66bcf-106">Member</span></span>|<span data-ttu-id="66bcf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66bcf-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="66bcf-108">Hodnota [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) výčet, který určuje typ výjimky klauzuli právě zadaný kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="66bcf-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="66bcf-109">Nativní vstupní bod obslužné rutiny klauzule – například obsah X86 EIP registru.</span><span class="sxs-lookup"><span data-stu-id="66bcf-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="66bcf-110">Ukazatel na logické rámce pro obslužnou rutinu klauzule – například obsah X86 EBP registru.</span><span class="sxs-lookup"><span data-stu-id="66bcf-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="66bcf-111">Ukazatel zásobníku stínové.</span><span class="sxs-lookup"><span data-stu-id="66bcf-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="66bcf-112">Tato hodnota je obsah registru BSP a se vztahuje pouze na IA64.</span><span class="sxs-lookup"><span data-stu-id="66bcf-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66bcf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66bcf-113">Remarks</span></span>  
 <span data-ttu-id="66bcf-114">Po přijetí oznámení o výjimce [ICorProfilerInfo2::getnotifiedexceptionclauseinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) lze použít k získání nativní adresy a rámce informací pro klauzuli výjimky (`catch` / `finally`/filter), má být spuštěna, nebo byla právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="66bcf-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="66bcf-115">Provádění klauzule výjimka zahrnuje tyto zpětná volání z common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="66bcf-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="66bcf-116">Icorprofilercallback::exceptioncatcherenter –</span><span class="sxs-lookup"><span data-stu-id="66bcf-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="66bcf-117">Icorprofilercallback::exceptionunwindfinallyenter –</span><span class="sxs-lookup"><span data-stu-id="66bcf-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="66bcf-118">Icorprofilercallback::exceptionsearchfilterenter –</span><span class="sxs-lookup"><span data-stu-id="66bcf-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="66bcf-119">Icorprofilercallback::exceptioncatcherleave –</span><span class="sxs-lookup"><span data-stu-id="66bcf-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="66bcf-120">Icorprofilercallback::exceptionunwindfinallyleave –</span><span class="sxs-lookup"><span data-stu-id="66bcf-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="66bcf-121">Icorprofilercallback::exceptionsearchfilterleave –</span><span class="sxs-lookup"><span data-stu-id="66bcf-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="66bcf-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66bcf-122">Requirements</span></span>  
 <span data-ttu-id="66bcf-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66bcf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66bcf-124">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="66bcf-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="66bcf-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66bcf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66bcf-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66bcf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66bcf-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="66bcf-127">See Also</span></span>  
 [<span data-ttu-id="66bcf-128">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="66bcf-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
