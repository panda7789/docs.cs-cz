---
title: CorDebugGenerationTypes – výčet
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1707a09f14fbab6150c2ecbcd188d7bf88064fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085893"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="9cfa6-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="9cfa6-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="9cfa6-103">Určuje generování oblast paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="9cfa6-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cfa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cfa6-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="9cfa6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9cfa6-105">Members</span></span>  
  
|<span data-ttu-id="9cfa6-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="9cfa6-106">Member name</span></span>|<span data-ttu-id="9cfa6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9cfa6-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="9cfa6-108">0. generace.</span><span class="sxs-lookup"><span data-stu-id="9cfa6-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="9cfa6-109">1. generace.</span><span class="sxs-lookup"><span data-stu-id="9cfa6-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="9cfa6-110">2. generace.</span><span class="sxs-lookup"><span data-stu-id="9cfa6-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="9cfa6-111">Haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="9cfa6-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cfa6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cfa6-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cfa6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cfa6-113">Requirements</span></span>  
 <span data-ttu-id="9cfa6-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cfa6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cfa6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cfa6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cfa6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cfa6-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9cfa6-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9cfa6-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cfa6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cfa6-118">See also</span></span>

- [<span data-ttu-id="9cfa6-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="9cfa6-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
