---
title: COR_PRF_TRANSITION_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867043"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="f7d65-102">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="f7d65-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="f7d65-103">Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="f7d65-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d65-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="f7d65-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f7d65-105">Members</span></span>  
  
|<span data-ttu-id="f7d65-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f7d65-106">Member</span></span>|<span data-ttu-id="f7d65-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f7d65-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="f7d65-108">Přechod je způsoben voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="f7d65-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="f7d65-109">Přechod je způsoben návratem z funkce.</span><span class="sxs-lookup"><span data-stu-id="f7d65-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7d65-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7d65-110">Remarks</span></span>  
 <span data-ttu-id="f7d65-111">Když dojde k přechodu, Profiler obdrží zpětné volání [ICorProfilerCallback:: ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) nebo [ICorProfilerCallback:: UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) , které poskytuje hodnotu výčtu `COR_PRF_TRANSITION_REASON` k označení důvodu přechodu.</span><span class="sxs-lookup"><span data-stu-id="f7d65-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d65-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7d65-112">Requirements</span></span>  
 <span data-ttu-id="f7d65-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d65-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d65-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f7d65-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7d65-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f7d65-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d65-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d65-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
