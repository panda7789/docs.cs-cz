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
ms.openlocfilehash: fe8be6a7c18fff54825f981672f0f640bb60c35c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482207"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="79420-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="79420-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="79420-103">Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="79420-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79420-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79420-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="79420-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79420-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="79420-106">Členové</span><span class="sxs-lookup"><span data-stu-id="79420-106">Members</span></span>  
  
|<span data-ttu-id="79420-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="79420-107">Member name</span></span>|<span data-ttu-id="79420-108">Popis</span><span class="sxs-lookup"><span data-stu-id="79420-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="79420-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="79420-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="79420-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="79420-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79420-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79420-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79420-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79420-112">Requirements</span></span>  
 <span data-ttu-id="79420-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79420-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79420-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79420-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79420-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79420-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79420-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79420-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79420-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79420-117">See also</span></span>
- [<span data-ttu-id="79420-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="79420-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
