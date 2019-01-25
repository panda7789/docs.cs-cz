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
ms.openlocfilehash: 49521e4b4ff5f8c364827b233759e163aca43e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542652"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="f7725-102">CorDebugBlockingObject – struktura</span><span class="sxs-lookup"><span data-stu-id="f7725-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="f7725-103">Definuje objekt, který blokuje vlákno a z určitého důvodu, že je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="f7725-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7725-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7725-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="f7725-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f7725-105">Members</span></span>  
  
|<span data-ttu-id="f7725-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f7725-106">Member</span></span>|<span data-ttu-id="f7725-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f7725-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="f7725-108">Objekt, na kterém je blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="f7725-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="f7725-109">Tento objekt je platný pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="f7725-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="f7725-110">Pokud se dvěma vlákny blokují na stejný objekt v rámci stejného synchronizovaného stavu, můžete očekávat [icordebugvalue::getaddress –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody vrátí stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7725-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="f7725-111">Rozhraní však může nebo nemusí být ukazatel ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="f7725-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="f7725-112">Počet milisekund před blokující operace způsobí vypršení časového limitu, nebo hodnota NEKONEČNO, což znamená, že bude omezen časovým limitem. Hodnota časového limitu určuje celkový čas blokující operace, bez času, který je stále zbývající.</span><span class="sxs-lookup"><span data-stu-id="f7725-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="f7725-113">Důvodu, že je vlákno blokované, u tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="f7725-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7725-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7725-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7725-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7725-115">Requirements</span></span>  
 <span data-ttu-id="f7725-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7725-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7725-117">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="f7725-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f7725-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7725-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7725-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7725-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7725-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7725-120">See also</span></span>
- [<span data-ttu-id="f7725-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7725-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f7725-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="f7725-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
