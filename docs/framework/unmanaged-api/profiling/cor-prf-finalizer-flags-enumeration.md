---
title: COR_PRF_FINALIZER_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: b273faafd7abb86ace58bb5c24473406af3ce20e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500969"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="08a57-102">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="08a57-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="08a57-103">Popisuje finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="08a57-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08a57-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="08a57-105">Členové</span><span class="sxs-lookup"><span data-stu-id="08a57-105">Members</span></span>  
  
|<span data-ttu-id="08a57-106">Člen</span><span class="sxs-lookup"><span data-stu-id="08a57-106">Member</span></span>|<span data-ttu-id="08a57-107">Description</span><span class="sxs-lookup"><span data-stu-id="08a57-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="08a57-108">Finalizační metoda je kritická.</span><span class="sxs-lookup"><span data-stu-id="08a57-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08a57-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08a57-109">Remarks</span></span>  
 <span data-ttu-id="08a57-110">`COR_PRF_FINALIZER_FLAGS`Výčet je používán metodou [ICorProfilerCallback2:: FinalizeableObjectQueued –](icorprofilercallback2-finalizeableobjectqueued-method.md) pro popis finalizační metody objektu.</span><span class="sxs-lookup"><span data-stu-id="08a57-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a57-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08a57-111">Requirements</span></span>  
 <span data-ttu-id="08a57-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a57-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a57-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="08a57-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08a57-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08a57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08a57-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a57-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a57-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08a57-116">See also</span></span>

- [<span data-ttu-id="08a57-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="08a57-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
