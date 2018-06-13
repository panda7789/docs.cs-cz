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
ms.openlocfilehash: ed7db321b32657087b791758096c692f25f3d7f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407833"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="44f03-102">CorDebugBlockingObject – struktura</span><span class="sxs-lookup"><span data-stu-id="44f03-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="44f03-103">Definuje objekt, který je blokování vlákna a určitého důvodu, že je blokované vlákno.</span><span class="sxs-lookup"><span data-stu-id="44f03-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44f03-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="44f03-105">Členové</span><span class="sxs-lookup"><span data-stu-id="44f03-105">Members</span></span>  
  
|<span data-ttu-id="44f03-106">Člen</span><span class="sxs-lookup"><span data-stu-id="44f03-106">Member</span></span>|<span data-ttu-id="44f03-107">Popis</span><span class="sxs-lookup"><span data-stu-id="44f03-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="44f03-108">Objekt, na kterém je blokování vlákno.</span><span class="sxs-lookup"><span data-stu-id="44f03-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="44f03-109">Tento objekt je platný pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="44f03-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="44f03-110">Pokud se dvěma vlákny blokují na stejný objekt v rámci stejné synchronizovaného stavu, můžete očekávat [icordebugvalue::getaddress –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metoda vrátí stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="44f03-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="44f03-111">Rozhraní však může nebo nemusí být ukazatel ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="44f03-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="44f03-112">Počet milisekund, po předtím, než blokování operace bude vypršení časového limitu, nebo hodnotu NEKONEČNÉ, který označuje, že ji není vypršení časového limitu. Hodnota časového limitu určuje celková délka čas blokování operace, není čas, který je stále zbývající.</span><span class="sxs-lookup"><span data-stu-id="44f03-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="44f03-113">Z důvodu, že je na tomto objektu blokované vlákno.</span><span class="sxs-lookup"><span data-stu-id="44f03-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f03-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44f03-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44f03-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44f03-115">Requirements</span></span>  
 <span data-ttu-id="44f03-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f03-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f03-117">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="44f03-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="44f03-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44f03-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44f03-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f03-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="44f03-120">See Also</span></span>  
 [<span data-ttu-id="44f03-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="44f03-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="44f03-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="44f03-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
