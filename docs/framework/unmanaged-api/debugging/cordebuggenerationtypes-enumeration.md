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
ms.openlocfilehash: 0443f58b79e60111756308cc4843daf86d1fc823
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795862"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="34e0d-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="34e0d-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="34e0d-103">Určuje generaci oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="34e0d-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34e0d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="34e0d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="34e0d-105">Members</span></span>  
  
|<span data-ttu-id="34e0d-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="34e0d-106">Member name</span></span>|<span data-ttu-id="34e0d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="34e0d-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="34e0d-108">Generace 0.</span><span class="sxs-lookup"><span data-stu-id="34e0d-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="34e0d-109">Generace 1.</span><span class="sxs-lookup"><span data-stu-id="34e0d-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="34e0d-110">Generace 2.</span><span class="sxs-lookup"><span data-stu-id="34e0d-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="34e0d-111">Halda velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="34e0d-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e0d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34e0d-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34e0d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34e0d-113">Requirements</span></span>  
 <span data-ttu-id="34e0d-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e0d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e0d-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34e0d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34e0d-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34e0d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34e0d-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34e0d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e0d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e0d-118">See also</span></span>

- [<span data-ttu-id="34e0d-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="34e0d-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
