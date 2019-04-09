---
title: CorDebugBlockingObject – struktura
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143218"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="4599d-102">CorDebugBlockingObject – struktura</span><span class="sxs-lookup"><span data-stu-id="4599d-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="4599d-103">Definuje objekt, který blokuje vlákno a z určitého důvodu, že je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="4599d-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4599d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4599d-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="4599d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4599d-105">Members</span></span>  
  
|<span data-ttu-id="4599d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4599d-106">Member</span></span>|<span data-ttu-id="4599d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4599d-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="4599d-108">Objekt, na kterém je blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="4599d-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="4599d-109">Tento objekt je platný pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="4599d-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="4599d-110">Pokud se dvěma vlákny blokují na stejný objekt v rámci stejného synchronizovaného stavu, můžete očekávat [icordebugvalue::getaddress –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody vrátí stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4599d-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="4599d-111">Rozhraní však může nebo nemusí být ukazatel ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4599d-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="4599d-112">Počet milisekund před blokující operace způsobí vypršení časového limitu, nebo hodnota NEKONEČNO, což znamená, že bude omezen časovým limitem. Hodnota časového limitu určuje celkový čas blokující operace, bez času, který je stále zbývající.</span><span class="sxs-lookup"><span data-stu-id="4599d-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="4599d-113">Důvodu, že je vlákno blokované, u tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="4599d-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4599d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4599d-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4599d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4599d-115">Requirements</span></span>  
 <span data-ttu-id="4599d-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4599d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4599d-117">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="4599d-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="4599d-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4599d-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4599d-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4599d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4599d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4599d-120">See also</span></span>

- [<span data-ttu-id="4599d-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="4599d-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4599d-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="4599d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
