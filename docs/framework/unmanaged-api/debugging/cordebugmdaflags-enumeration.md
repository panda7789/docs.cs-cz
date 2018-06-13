---
title: CorDebugMDAFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac4a8a0c13ba6aa0d5c65ec7fa1aa3b771c964eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404856"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="580a8-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="580a8-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="580a8-103">Určuje stav vláken, na kterém je aktivována, Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="580a8-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="580a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="580a8-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="580a8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="580a8-105">Members</span></span>  
  
|<span data-ttu-id="580a8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="580a8-106">Member</span></span>|<span data-ttu-id="580a8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="580a8-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="580a8-108">Vlákno, na kterém byl MDA aktivováno opožděný vzhledem k tomu, že MDA byla aktivována.</span><span class="sxs-lookup"><span data-stu-id="580a8-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="580a8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="580a8-109">Remarks</span></span>  
 <span data-ttu-id="580a8-110">Když zásobníku volání už popisuje, kde byla původně vyvolána MDA, vlákno má mít *opožděný*.</span><span class="sxs-lookup"><span data-stu-id="580a8-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="580a8-111">Jedná se neobvyklé okolnosti způsobené provádění vlákna na neplatnou operaci vyprázdněna.</span><span class="sxs-lookup"><span data-stu-id="580a8-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="580a8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="580a8-112">Requirements</span></span>  
 <span data-ttu-id="580a8-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="580a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="580a8-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="580a8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="580a8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="580a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="580a8-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="580a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580a8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="580a8-117">See Also</span></span>  
 [<span data-ttu-id="580a8-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="580a8-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
