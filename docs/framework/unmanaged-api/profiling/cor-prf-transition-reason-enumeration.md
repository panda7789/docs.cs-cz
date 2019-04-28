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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599036"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="f57ad-102">COR_PRF_TRANSITION_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="f57ad-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="f57ad-103">Označuje důvod pro přechod ze spravovaného do nespravovaného kódu a naopak.</span><span class="sxs-lookup"><span data-stu-id="f57ad-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57ad-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="f57ad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f57ad-105">Members</span></span>  
  
|<span data-ttu-id="f57ad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f57ad-106">Member</span></span>|<span data-ttu-id="f57ad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f57ad-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="f57ad-108">Tento přechod je kvůli volání funkce.</span><span class="sxs-lookup"><span data-stu-id="f57ad-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="f57ad-109">Tento přechod je kvůli vrácení z funkce.</span><span class="sxs-lookup"><span data-stu-id="f57ad-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f57ad-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f57ad-110">Remarks</span></span>  
 <span data-ttu-id="f57ad-111">Pokud dojde k přechodu, profiler obdrží [icorprofilercallback::managedtounmanagedtransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) nebo [icorprofilercallback::unmanagedtomanagedtransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) zpětné volání, každý z nich poskytuje hodnotu `COR_PRF_TRANSITION_REASON` výčet označující důvod pro přechod.</span><span class="sxs-lookup"><span data-stu-id="f57ad-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57ad-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f57ad-112">Requirements</span></span>  
 <span data-ttu-id="f57ad-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f57ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57ad-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f57ad-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f57ad-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f57ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f57ad-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f57ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
