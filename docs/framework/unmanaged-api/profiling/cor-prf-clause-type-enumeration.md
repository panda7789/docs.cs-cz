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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775190"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="b5020-102">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="b5020-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="b5020-103">Určuje typ výjimky klauzuli, která je právě zadali kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="b5020-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5020-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5020-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b5020-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b5020-105">Members</span></span>  
  
|<span data-ttu-id="b5020-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b5020-106">Member</span></span>|<span data-ttu-id="b5020-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b5020-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="b5020-108">Klauzule výjimka není platná.</span><span class="sxs-lookup"><span data-stu-id="b5020-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="b5020-109">V klauzuli výjimka je výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="b5020-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="b5020-110">Klauzule výjimka je `catch` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b5020-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="b5020-111">Klauzule výjimka je `finally` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b5020-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5020-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5020-112">Requirements</span></span>  
 <span data-ttu-id="b5020-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5020-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5020-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5020-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5020-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5020-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5020-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5020-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5020-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5020-117">See also</span></span>

- [<span data-ttu-id="b5020-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b5020-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
