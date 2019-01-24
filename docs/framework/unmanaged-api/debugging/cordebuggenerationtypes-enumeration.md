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
ms.openlocfilehash: 5fb663bc17458f0866e66332e40527390714fc79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720442"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="7207e-102">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="7207e-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="7207e-103">Určuje generování oblast paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7207e-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7207e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7207e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="7207e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7207e-105">Members</span></span>  
  
|<span data-ttu-id="7207e-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="7207e-106">Member name</span></span>|<span data-ttu-id="7207e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7207e-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="7207e-108">0. generace.</span><span class="sxs-lookup"><span data-stu-id="7207e-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="7207e-109">1. generace.</span><span class="sxs-lookup"><span data-stu-id="7207e-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="7207e-110">2. generace.</span><span class="sxs-lookup"><span data-stu-id="7207e-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="7207e-111">Haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="7207e-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7207e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7207e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7207e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7207e-113">Requirements</span></span>  
 <span data-ttu-id="7207e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7207e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7207e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7207e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7207e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7207e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7207e-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7207e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7207e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7207e-118">See also</span></span>
- [<span data-ttu-id="7207e-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7207e-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
