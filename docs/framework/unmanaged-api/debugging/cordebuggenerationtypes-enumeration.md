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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989661"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="fb3d1-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="fb3d1-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="fb3d1-103">Určuje generování oblast paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="fb3d1-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb3d1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="fb3d1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fb3d1-105">Members</span></span>  
  
|<span data-ttu-id="fb3d1-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="fb3d1-106">Member name</span></span>|<span data-ttu-id="fb3d1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fb3d1-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="fb3d1-108">0. generace.</span><span class="sxs-lookup"><span data-stu-id="fb3d1-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="fb3d1-109">1. generace.</span><span class="sxs-lookup"><span data-stu-id="fb3d1-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="fb3d1-110">2. generace.</span><span class="sxs-lookup"><span data-stu-id="fb3d1-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="fb3d1-111">Haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="fb3d1-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3d1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb3d1-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb3d1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb3d1-113">Requirements</span></span>  
 <span data-ttu-id="fb3d1-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3d1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3d1-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb3d1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb3d1-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb3d1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb3d1-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3d1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3d1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb3d1-118">See also</span></span>

- [<span data-ttu-id="fb3d1-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb3d1-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
