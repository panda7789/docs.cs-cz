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
ms.openlocfilehash: e024500ea66dcb42e712e07e976a709401160a27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795765"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="e44f4-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="e44f4-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="e44f4-103">Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="e44f4-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e44f4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e44f4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e44f4-105">Members</span></span>  
  
|<span data-ttu-id="e44f4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e44f4-106">Member</span></span>|<span data-ttu-id="e44f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e44f4-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="e44f4-108">Vlákno, ve kterém se aktivovalo MDA, bylo od chvíle, kdy byla vyvolána služba MDA, naproti skluzu.</span><span class="sxs-lookup"><span data-stu-id="e44f4-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e44f4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e44f4-109">Remarks</span></span>  
 <span data-ttu-id="e44f4-110">V případě, že zásobník volání již nepopisuje, kde byl původně vyvolán proces MDA, vlákno je *slipped*považováno za neúspěšně.</span><span class="sxs-lookup"><span data-stu-id="e44f4-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="e44f4-111">Jedná se o neobvyklé okolnosti, o jejichž provedení neplatného vlákna po ukončení operace.</span><span class="sxs-lookup"><span data-stu-id="e44f4-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e44f4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e44f4-112">Requirements</span></span>  
 <span data-ttu-id="e44f4-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e44f4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e44f4-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e44f4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e44f4-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e44f4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e44f4-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e44f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44f4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e44f4-117">See also</span></span>

- [<span data-ttu-id="e44f4-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="e44f4-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
