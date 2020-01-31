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
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867266"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="ecddb-102">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="ecddb-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="ecddb-103">Popisuje finalizační metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecddb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="ecddb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ecddb-105">Members</span></span>  
  
|<span data-ttu-id="ecddb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ecddb-106">Member</span></span>|<span data-ttu-id="ecddb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ecddb-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="ecddb-108">Finalizační metoda je kritická.</span><span class="sxs-lookup"><span data-stu-id="ecddb-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecddb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecddb-109">Remarks</span></span>  
 <span data-ttu-id="ecddb-110">Výčet `COR_PRF_FINALIZER_FLAGS` používá metoda [ICorProfilerCallback2:: FinalizeableObjectQueued –](icorprofilercallback2-finalizeableobjectqueued-method.md) k popisu finalizační metody objektu.</span><span class="sxs-lookup"><span data-stu-id="ecddb-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecddb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecddb-111">Requirements</span></span>  
 <span data-ttu-id="ecddb-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecddb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecddb-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ecddb-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ecddb-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecddb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecddb-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecddb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecddb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecddb-116">See also</span></span>

- [<span data-ttu-id="ecddb-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ecddb-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
