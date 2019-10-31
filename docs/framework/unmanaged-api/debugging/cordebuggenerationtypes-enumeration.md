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
ms.openlocfilehash: 362e917e1684c91bde80a8b5c2e6a27a18a99190
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098202"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="32424-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="32424-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="32424-103">Určuje generaci oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="32424-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32424-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32424-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="32424-105">Členové</span><span class="sxs-lookup"><span data-stu-id="32424-105">Members</span></span>  
  
|<span data-ttu-id="32424-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="32424-106">Member name</span></span>|<span data-ttu-id="32424-107">Popis</span><span class="sxs-lookup"><span data-stu-id="32424-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="32424-108">Generace 0.</span><span class="sxs-lookup"><span data-stu-id="32424-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="32424-109">Generace 1.</span><span class="sxs-lookup"><span data-stu-id="32424-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="32424-110">Generace 2.</span><span class="sxs-lookup"><span data-stu-id="32424-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="32424-111">Halda velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="32424-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32424-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32424-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32424-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32424-113">Requirements</span></span>  
 <span data-ttu-id="32424-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32424-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32424-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32424-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32424-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32424-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32424-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32424-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32424-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32424-118">See also</span></span>

- [<span data-ttu-id="32424-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="32424-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
