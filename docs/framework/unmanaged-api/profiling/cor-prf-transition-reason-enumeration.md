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
ms.openlocfilehash: e890c62a54654e86bb4a825613807efe142c8d5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500738"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="c6087-102">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="c6087-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="c6087-103">Označuje důvod přechodu ze spravovaného do nespravovaného kódu nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="c6087-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6087-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6087-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="c6087-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c6087-105">Members</span></span>  
  
|<span data-ttu-id="c6087-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c6087-106">Member</span></span>|<span data-ttu-id="c6087-107">Description</span><span class="sxs-lookup"><span data-stu-id="c6087-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="c6087-108">Přechod je způsoben voláním funkce.</span><span class="sxs-lookup"><span data-stu-id="c6087-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="c6087-109">Přechod je způsoben návratem z funkce.</span><span class="sxs-lookup"><span data-stu-id="c6087-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6087-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6087-110">Remarks</span></span>  
 <span data-ttu-id="c6087-111">Když dojde k přechodu, Profiler obdrží zpětné volání [ICorProfilerCallback:: ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) nebo [ICorProfilerCallback:: UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) , z nichž každá poskytuje hodnotu `COR_PRF_TRANSITION_REASON` výčtu k označení důvodu přechodu.</span><span class="sxs-lookup"><span data-stu-id="c6087-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6087-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6087-112">Requirements</span></span>  
 <span data-ttu-id="c6087-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6087-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6087-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6087-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6087-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6087-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6087-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6087-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
