---
title: COR_PRF_CLAUSE_TYPE – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: edf5d61baae28a82aff0d0bd32d1d900085ac375
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867318"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="4b5e5-102">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="4b5e5-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="4b5e5-103">Určuje typ klauzule Exception, kterou kód právě zadal, nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="4b5e5-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b5e5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="4b5e5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4b5e5-105">Members</span></span>  
  
|<span data-ttu-id="4b5e5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4b5e5-106">Member</span></span>|<span data-ttu-id="4b5e5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4b5e5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="4b5e5-108">Klauzule Exception není platná.</span><span class="sxs-lookup"><span data-stu-id="4b5e5-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="4b5e5-109">Klauzule Exception je výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="4b5e5-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="4b5e5-110">Klauzule Exception je příkaz `catch`.</span><span class="sxs-lookup"><span data-stu-id="4b5e5-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="4b5e5-111">Klauzule Exception je příkaz `finally`.</span><span class="sxs-lookup"><span data-stu-id="4b5e5-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b5e5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b5e5-112">Requirements</span></span>  
 <span data-ttu-id="4b5e5-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b5e5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b5e5-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4b5e5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b5e5-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b5e5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b5e5-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b5e5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b5e5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b5e5-117">See also</span></span>

- [<span data-ttu-id="4b5e5-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4b5e5-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
