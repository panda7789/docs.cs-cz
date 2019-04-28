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
ms.openlocfilehash: 02ff60852a85d003deb68cae96a184ac8d61c65f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609396"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="15d22-102">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="15d22-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="15d22-103">Určuje typ procesu vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="15d22-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15d22-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="15d22-105">Členové</span><span class="sxs-lookup"><span data-stu-id="15d22-105">Members</span></span>  
  
|<span data-ttu-id="15d22-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="15d22-106">Member name</span></span>|<span data-ttu-id="15d22-107">Popis</span><span class="sxs-lookup"><span data-stu-id="15d22-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="15d22-108">Spravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="15d22-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15d22-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15d22-109">Remarks</span></span>  
 <span data-ttu-id="15d22-110">Aktuální verze rozhraní API pro nespravované ladění zobrazí pouze pro spravované procesy.</span><span class="sxs-lookup"><span data-stu-id="15d22-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d22-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15d22-111">Requirements</span></span>  
 <span data-ttu-id="15d22-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d22-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="15d22-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="15d22-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15d22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d22-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d22-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d22-116">See also</span></span>

- [<span data-ttu-id="15d22-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="15d22-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
