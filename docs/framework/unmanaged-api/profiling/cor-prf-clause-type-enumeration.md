---
title: "COR_PRF_CLAUSE_TYPE – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CLAUSE_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CLAUSE_TYPE
helpviewer_keywords: COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bd34422656432b9bf8939b81ca0a8583c9d08e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="d59d6-102">COR_PRF_CLAUSE_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="d59d6-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="d59d6-103">Určuje typ výjimky klauzuli, který právě zadán kód nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="d59d6-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d59d6-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d59d6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d59d6-105">Members</span></span>  
  
|<span data-ttu-id="d59d6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d59d6-106">Member</span></span>|<span data-ttu-id="d59d6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d59d6-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="d59d6-108">V klauzuli výjimka není platný.</span><span class="sxs-lookup"><span data-stu-id="d59d6-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="d59d6-109">V klauzuli výjimka je výraz filtru.</span><span class="sxs-lookup"><span data-stu-id="d59d6-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="d59d6-110">Je v klauzuli výjimky `catch` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d59d6-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="d59d6-111">Je v klauzuli výjimky `finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="d59d6-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d59d6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d59d6-112">Requirements</span></span>  
 <span data-ttu-id="d59d6-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59d6-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d59d6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d59d6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d59d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d59d6-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59d6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d59d6-117">See Also</span></span>  
 [<span data-ttu-id="d59d6-118">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="d59d6-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
