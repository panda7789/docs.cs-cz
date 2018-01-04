---
title: "CorDebugMDAFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMDAFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMDAFlags
helpviewer_keywords: CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: defd2572d6f925cf557539983308b3b3e900eebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="cc518-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="cc518-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="cc518-103">Určuje stav vláken, na kterém je aktivována, Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="cc518-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc518-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc518-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cc518-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cc518-105">Members</span></span>  
  
|<span data-ttu-id="cc518-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cc518-106">Member</span></span>|<span data-ttu-id="cc518-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cc518-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="cc518-108">Vlákno, na kterém byl MDA aktivováno opožděný vzhledem k tomu, že MDA byla aktivována.</span><span class="sxs-lookup"><span data-stu-id="cc518-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc518-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc518-109">Remarks</span></span>  
 <span data-ttu-id="cc518-110">Když zásobníku volání už popisuje, kde byla původně vyvolána MDA, vlákno má mít *opožděný*.</span><span class="sxs-lookup"><span data-stu-id="cc518-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="cc518-111">Jedná se neobvyklé okolnosti způsobené provádění vlákna na neplatnou operaci vyprázdněna.</span><span class="sxs-lookup"><span data-stu-id="cc518-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc518-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc518-112">Requirements</span></span>  
 <span data-ttu-id="cc518-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc518-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc518-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc518-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc518-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc518-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc518-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc518-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc518-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc518-117">See Also</span></span>  
 [<span data-ttu-id="cc518-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="cc518-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
