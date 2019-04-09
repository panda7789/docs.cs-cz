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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14d42a4032c3e2b1c231414678912e1658e759d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101722"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="848c8-102">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="848c8-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="848c8-103">Poskytuje reprezentaci jedinečné funkce kombinací jeho ID, identifikátorem její překompilovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="848c8-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="848c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="848c8-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="848c8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="848c8-105">Members</span></span>  
  
|<span data-ttu-id="848c8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="848c8-106">Member</span></span>|<span data-ttu-id="848c8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="848c8-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="848c8-108">ID funkce.</span><span class="sxs-lookup"><span data-stu-id="848c8-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="848c8-109">ID znovu kompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="848c8-109">The ID of the recompiled function.</span></span> <span data-ttu-id="848c8-110">Hodnota 0 (nula) představuje původní verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="848c8-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="848c8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="848c8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="848c8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="848c8-112">Requirements</span></span>  
 <span data-ttu-id="848c8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="848c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="848c8-114">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="848c8-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="848c8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="848c8-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="848c8-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="848c8-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="848c8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="848c8-117">See also</span></span>

- [<span data-ttu-id="848c8-118">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="848c8-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
