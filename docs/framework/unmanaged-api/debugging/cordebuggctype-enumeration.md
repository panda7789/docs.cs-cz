---
title: CorDebugGCType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182920"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="de644-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="de644-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="de644-103">Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="de644-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de644-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de644-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="de644-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de644-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="de644-106">Členové</span><span class="sxs-lookup"><span data-stu-id="de644-106">Members</span></span>  
  
|<span data-ttu-id="de644-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="de644-107">Member name</span></span>|<span data-ttu-id="de644-108">Popis</span><span class="sxs-lookup"><span data-stu-id="de644-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="de644-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="de644-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="de644-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="de644-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de644-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de644-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de644-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de644-112">Requirements</span></span>  
 <span data-ttu-id="de644-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de644-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de644-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de644-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de644-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de644-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de644-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de644-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de644-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de644-117">See also</span></span>

- [<span data-ttu-id="de644-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="de644-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
