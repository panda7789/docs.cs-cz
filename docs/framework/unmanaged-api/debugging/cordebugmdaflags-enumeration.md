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
ms.openlocfilehash: 732523935eec62bffbc15705bc93c97f14c90064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148418"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="478da-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="478da-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="478da-103">Určuje stav vláken, ve kterém se spustí Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="478da-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="478da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="478da-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="478da-105">Členové</span><span class="sxs-lookup"><span data-stu-id="478da-105">Members</span></span>  
  
|<span data-ttu-id="478da-106">Člen</span><span class="sxs-lookup"><span data-stu-id="478da-106">Member</span></span>|<span data-ttu-id="478da-107">Popis</span><span class="sxs-lookup"><span data-stu-id="478da-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="478da-108">Vlákno, na kterém se vyvolala MDA opožděný vzhledem k tomu, že se vyvolala MDA.</span><span class="sxs-lookup"><span data-stu-id="478da-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="478da-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="478da-109">Remarks</span></span>  
 <span data-ttu-id="478da-110">Když zásobník volání již popisuje, kde byla původně vyvolána MDA, vlákno se považuje za mít *opožděný*.</span><span class="sxs-lookup"><span data-stu-id="478da-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="478da-111">Toto je neobvyklé okolnosti způsobené vlákna provádění neplatné operace ukončením.</span><span class="sxs-lookup"><span data-stu-id="478da-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="478da-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="478da-112">Requirements</span></span>  
 <span data-ttu-id="478da-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="478da-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="478da-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="478da-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="478da-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="478da-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="478da-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="478da-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="478da-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="478da-117">See also</span></span>

- [<span data-ttu-id="478da-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="478da-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
