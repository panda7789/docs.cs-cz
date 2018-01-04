---
title: "CorDebugGenerationTypes – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGenerationTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGenerationTypes
helpviewer_keywords: CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9b5126958b17ee2d1de5394ed07d78c3ffe29b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="930fd-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="930fd-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="930fd-103">Spravovaná halda určuje generování oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="930fd-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="930fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="930fd-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="930fd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="930fd-105">Members</span></span>  
  
|<span data-ttu-id="930fd-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="930fd-106">Member name</span></span>|<span data-ttu-id="930fd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="930fd-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="930fd-108">0. generace.</span><span class="sxs-lookup"><span data-stu-id="930fd-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="930fd-109">Generace 1.</span><span class="sxs-lookup"><span data-stu-id="930fd-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="930fd-110">2. generace.</span><span class="sxs-lookup"><span data-stu-id="930fd-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="930fd-111">Halda velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="930fd-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="930fd-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="930fd-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="930fd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="930fd-113">Requirements</span></span>  
 <span data-ttu-id="930fd-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="930fd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="930fd-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="930fd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="930fd-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="930fd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="930fd-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="930fd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930fd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="930fd-118">See Also</span></span>  
 [<span data-ttu-id="930fd-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="930fd-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
