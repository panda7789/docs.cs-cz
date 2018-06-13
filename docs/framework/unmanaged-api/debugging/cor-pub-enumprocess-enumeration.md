---
title: COR_PUB_ENUMPROCESS – výčet
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcdb5883e109d7e0c73c8fb76ee61b52cf23091f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406998"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="6512d-102">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="6512d-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="6512d-103">Určuje typ procesu výčet.</span><span class="sxs-lookup"><span data-stu-id="6512d-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6512d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6512d-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="6512d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6512d-105">Members</span></span>  
  
|<span data-ttu-id="6512d-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="6512d-106">Member name</span></span>|<span data-ttu-id="6512d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6512d-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="6512d-108">Spravované proces.</span><span class="sxs-lookup"><span data-stu-id="6512d-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6512d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6512d-109">Remarks</span></span>  
 <span data-ttu-id="6512d-110">Aktuální verze nespravovaného rozhraní API pro ladění zobrazí jenom spravovaných procesy.</span><span class="sxs-lookup"><span data-stu-id="6512d-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6512d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6512d-111">Requirements</span></span>  
 <span data-ttu-id="6512d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6512d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6512d-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6512d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6512d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6512d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6512d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6512d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6512d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6512d-116">See Also</span></span>  
 [<span data-ttu-id="6512d-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="6512d-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
