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
ms.openlocfilehash: 098aaca8ec318b08c87e30c2a9558b7e64494a4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581999"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="655bb-102">COR_PRF_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="655bb-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="655bb-103">Poskytuje reprezentaci jedinečné funkce kombinací jeho ID, identifikátorem její překompilovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="655bb-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="655bb-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="655bb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="655bb-105">Members</span></span>  
  
|<span data-ttu-id="655bb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="655bb-106">Member</span></span>|<span data-ttu-id="655bb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="655bb-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="655bb-108">ID funkce.</span><span class="sxs-lookup"><span data-stu-id="655bb-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="655bb-109">ID znovu kompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="655bb-109">The ID of the recompiled function.</span></span> <span data-ttu-id="655bb-110">Hodnota 0 (nula) představuje původní verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="655bb-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655bb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="655bb-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="655bb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="655bb-112">Requirements</span></span>  
 <span data-ttu-id="655bb-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="655bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="655bb-114">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="655bb-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="655bb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="655bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="655bb-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="655bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655bb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="655bb-117">See also</span></span>
- [<span data-ttu-id="655bb-118">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="655bb-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
