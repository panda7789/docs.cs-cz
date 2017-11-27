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
ms.openlocfilehash: 827825e4012b421caa4e05702a6f1a1b863ac69d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="713e3-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="713e3-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="713e3-103">Určuje stav vláken, na kterém je aktivována, Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="713e3-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="713e3-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="713e3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="713e3-105">Members</span></span>  
  
|<span data-ttu-id="713e3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="713e3-106">Member</span></span>|<span data-ttu-id="713e3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="713e3-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="713e3-108">Vlákno, na kterém byl MDA aktivováno opožděný vzhledem k tomu, že MDA byla aktivována.</span><span class="sxs-lookup"><span data-stu-id="713e3-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="713e3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="713e3-109">Remarks</span></span>  
 <span data-ttu-id="713e3-110">Když zásobníku volání už popisuje, kde byla původně vyvolána MDA, vlákno má mít *opožděný*.</span><span class="sxs-lookup"><span data-stu-id="713e3-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="713e3-111">Jedná se neobvyklé okolnosti způsobené provádění vlákna na neplatnou operaci vyprázdněna.</span><span class="sxs-lookup"><span data-stu-id="713e3-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713e3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="713e3-112">Requirements</span></span>  
 <span data-ttu-id="713e3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="713e3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="713e3-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="713e3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="713e3-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="713e3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="713e3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="713e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713e3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="713e3-117">See Also</span></span>  
 [<span data-ttu-id="713e3-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="713e3-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
