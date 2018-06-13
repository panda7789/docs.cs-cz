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
ms.openlocfilehash: e74f564a483d80fd6312cf015802750d48e73ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403987"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="b8752-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="b8752-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="b8752-103">Určuje, zda má systém uvolňování běží na pracovní stanici nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="b8752-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8752-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8752-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8752-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8752-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="b8752-106">Členové</span><span class="sxs-lookup"><span data-stu-id="b8752-106">Members</span></span>  
  
|<span data-ttu-id="b8752-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="b8752-107">Member name</span></span>|<span data-ttu-id="b8752-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b8752-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="b8752-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="b8752-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="b8752-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="b8752-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8752-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8752-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8752-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8752-112">Requirements</span></span>  
 <span data-ttu-id="b8752-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8752-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8752-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8752-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8752-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8752-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8752-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8752-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8752-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8752-117">See Also</span></span>  
 [<span data-ttu-id="b8752-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="b8752-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
