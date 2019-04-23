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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101722"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="4654c-102">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="4654c-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="4654c-103">Poskytuje reprezentaci jedinečné funkce kombinací jeho ID, identifikátorem její překompilovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="4654c-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4654c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4654c-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="4654c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4654c-105">Members</span></span>  
  
|<span data-ttu-id="4654c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4654c-106">Member</span></span>|<span data-ttu-id="4654c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4654c-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="4654c-108">ID funkce.</span><span class="sxs-lookup"><span data-stu-id="4654c-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="4654c-109">ID znovu kompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="4654c-109">The ID of the recompiled function.</span></span> <span data-ttu-id="4654c-110">Hodnota 0 (nula) představuje původní verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="4654c-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4654c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4654c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4654c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4654c-112">Requirements</span></span>  
 <span data-ttu-id="4654c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4654c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4654c-114">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4654c-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4654c-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4654c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4654c-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4654c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4654c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4654c-117">See also</span></span>

- [<span data-ttu-id="4654c-118">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4654c-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
