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
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501050"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="3d5bf-102">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="3d5bf-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="3d5bf-103">Určuje typ klauzule Exception, kterou kód právě zadal, nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="3d5bf-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d5bf-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="3d5bf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3d5bf-105">Members</span></span>  
  
|<span data-ttu-id="3d5bf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3d5bf-106">Member</span></span>|<span data-ttu-id="3d5bf-107">Description</span><span class="sxs-lookup"><span data-stu-id="3d5bf-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="3d5bf-108">Klauzule Exception není platná.</span><span class="sxs-lookup"><span data-stu-id="3d5bf-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="3d5bf-109">Klauzule Exception je výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="3d5bf-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="3d5bf-110">Klauzule Exception je `catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="3d5bf-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="3d5bf-111">Klauzule Exception je `finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="3d5bf-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d5bf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d5bf-112">Requirements</span></span>  
 <span data-ttu-id="3d5bf-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d5bf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d5bf-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3d5bf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d5bf-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3d5bf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d5bf-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d5bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5bf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d5bf-117">See also</span></span>

- [<span data-ttu-id="3d5bf-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3d5bf-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
