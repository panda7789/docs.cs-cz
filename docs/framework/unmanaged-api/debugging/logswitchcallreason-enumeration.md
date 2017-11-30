---
title: "LogSwitchCallReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LogSwitchCallReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: LogSwitchCallReason
helpviewer_keywords: LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 937b26efa79605b585c420db608a938b3ee71f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="af043-102">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="af043-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="af043-103">Určuje operaci, která byla provedena na přepínači ladění nebo trasování.</span><span class="sxs-lookup"><span data-stu-id="af043-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af043-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="af043-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af043-105">Members</span></span>  
  
|<span data-ttu-id="af043-106">Člen</span><span class="sxs-lookup"><span data-stu-id="af043-106">Member</span></span>|<span data-ttu-id="af043-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af043-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="af043-108">Ladění nebo trasování přepínače byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="af043-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="af043-109">Přepínač ladění nebo trasování bylo změněno.</span><span class="sxs-lookup"><span data-stu-id="af043-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="af043-110">Ladění nebo trasování přepínačů bylo odstraněno.</span><span class="sxs-lookup"><span data-stu-id="af043-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af043-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af043-111">Requirements</span></span>  
 <span data-ttu-id="af043-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af043-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af043-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af043-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af043-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af043-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af043-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af043-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af043-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="af043-116">See Also</span></span>  
 [<span data-ttu-id="af043-117">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="af043-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
