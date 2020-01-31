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
ms.openlocfilehash: 6f4c96517375df4cd249b72953bf37812a498c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789365"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="771c8-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="771c8-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="771c8-103">Označuje, zda systém uvolňování paměti běží na pracovní stanici nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="771c8-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="771c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="771c8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="771c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="771c8-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="771c8-106">Členové</span><span class="sxs-lookup"><span data-stu-id="771c8-106">Members</span></span>  
  
|<span data-ttu-id="771c8-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="771c8-107">Member name</span></span>|<span data-ttu-id="771c8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="771c8-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="771c8-109">Systém uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="771c8-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="771c8-110">Systém uvolňování paměti je spuštěn na serveru.</span><span class="sxs-lookup"><span data-stu-id="771c8-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="771c8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="771c8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="771c8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="771c8-112">Requirements</span></span>  
 <span data-ttu-id="771c8-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="771c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="771c8-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="771c8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="771c8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="771c8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="771c8-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="771c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771c8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="771c8-117">See also</span></span>

- [<span data-ttu-id="771c8-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="771c8-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
