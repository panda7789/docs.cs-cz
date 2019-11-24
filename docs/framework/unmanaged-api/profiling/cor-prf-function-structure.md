---
title: COR_PRF_FUNCTION – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 40698a49ac7012c4f67eb88b1ead04c80f3dea77
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428324"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="ab90c-102">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="ab90c-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="ab90c-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span><span class="sxs-lookup"><span data-stu-id="ab90c-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab90c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab90c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ab90c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ab90c-105">Members</span></span>  
  
|<span data-ttu-id="ab90c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ab90c-106">Member</span></span>|<span data-ttu-id="ab90c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ab90c-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="ab90c-108">The ID of the function.</span><span class="sxs-lookup"><span data-stu-id="ab90c-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="ab90c-109">The ID of the recompiled function.</span><span class="sxs-lookup"><span data-stu-id="ab90c-109">The ID of the recompiled function.</span></span> <span data-ttu-id="ab90c-110">A value of 0 (zero) represents the original version of the function.</span><span class="sxs-lookup"><span data-stu-id="ab90c-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab90c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab90c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab90c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab90c-112">Requirements</span></span>  
 <span data-ttu-id="ab90c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab90c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab90c-114">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ab90c-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ab90c-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab90c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab90c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab90c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab90c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab90c-117">See also</span></span>

- [<span data-ttu-id="ab90c-118">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ab90c-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
