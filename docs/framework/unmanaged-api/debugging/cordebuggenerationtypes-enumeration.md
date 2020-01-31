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
ms.openlocfilehash: 6133b34a60fd06c1b75d69783760741b8de62071
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789345"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="2f7ed-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="2f7ed-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="2f7ed-103">Určuje generaci oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="2f7ed-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f7ed-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="2f7ed-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2f7ed-105">Members</span></span>  
  
|<span data-ttu-id="2f7ed-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="2f7ed-106">Member name</span></span>|<span data-ttu-id="2f7ed-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7ed-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="2f7ed-108">Generace 0.</span><span class="sxs-lookup"><span data-stu-id="2f7ed-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="2f7ed-109">Generace 1.</span><span class="sxs-lookup"><span data-stu-id="2f7ed-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="2f7ed-110">Generace 2.</span><span class="sxs-lookup"><span data-stu-id="2f7ed-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="2f7ed-111">Halda velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="2f7ed-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f7ed-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f7ed-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f7ed-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f7ed-113">Requirements</span></span>  
 <span data-ttu-id="2f7ed-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f7ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f7ed-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f7ed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f7ed-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f7ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f7ed-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f7ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7ed-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f7ed-118">See also</span></span>

- [<span data-ttu-id="2f7ed-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="2f7ed-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
