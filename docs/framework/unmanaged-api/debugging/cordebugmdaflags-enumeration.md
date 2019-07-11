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
ms.openlocfilehash: bf9f7f3d3419efc9e1dc7d75fc7272432c0cf5d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739690"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="773c5-102">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="773c5-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="773c5-103">Určuje stav vláken, ve kterém se spustí Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="773c5-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="773c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="773c5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="773c5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="773c5-105">Members</span></span>  
  
|<span data-ttu-id="773c5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="773c5-106">Member</span></span>|<span data-ttu-id="773c5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="773c5-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="773c5-108">Vlákno, na kterém se vyvolala MDA opožděný vzhledem k tomu, že se vyvolala MDA.</span><span class="sxs-lookup"><span data-stu-id="773c5-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="773c5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="773c5-109">Remarks</span></span>  
 <span data-ttu-id="773c5-110">Když zásobník volání již popisuje, kde byla původně vyvolána MDA, vlákno se považuje za mít *opožděný*.</span><span class="sxs-lookup"><span data-stu-id="773c5-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="773c5-111">Toto je neobvyklé okolnosti způsobené vlákna provádění neplatné operace ukončením.</span><span class="sxs-lookup"><span data-stu-id="773c5-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="773c5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="773c5-112">Requirements</span></span>  
 <span data-ttu-id="773c5-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="773c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="773c5-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="773c5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="773c5-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="773c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="773c5-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="773c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="773c5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="773c5-117">See also</span></span>

- [<span data-ttu-id="773c5-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="773c5-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
