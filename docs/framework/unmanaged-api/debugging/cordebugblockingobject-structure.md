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
ms.openlocfilehash: 21f90e06b3b02ebc6c97610b6edc35697601f0ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132292"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="af345-102">CorDebugBlockingObject – struktura</span><span class="sxs-lookup"><span data-stu-id="af345-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="af345-103">Definuje objekt, který blokuje vlákno, a konkrétní důvod, proč je vlákno blokované.</span><span class="sxs-lookup"><span data-stu-id="af345-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af345-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af345-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="af345-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af345-105">Members</span></span>  
  
|<span data-ttu-id="af345-106">Člen</span><span class="sxs-lookup"><span data-stu-id="af345-106">Member</span></span>|<span data-ttu-id="af345-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af345-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="af345-108">Objekt, na kterém vlákno blokuje.</span><span class="sxs-lookup"><span data-stu-id="af345-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="af345-109">Tento objekt je platný pouze po dobu trvání aktuálního synchronizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="af345-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="af345-110">Pokud jsou dvě vlákna blokována u stejného objektu ve stejném synchronizovaném stavu, může být očekávána metoda [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) , která vrací stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="af345-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="af345-111">Rozhraní však mohou nebo nemusí být ekvivalentem ukazatele.</span><span class="sxs-lookup"><span data-stu-id="af345-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="af345-112">Počet milisekund, po jejichž uplynutí vyprší časový limit operace blokování, nebo hodnota nekonečno, což znamená, že nedojde k vypršení časového limitu. Hodnota časového limitu určuje celkovou dobu blokující operace, nikoli čas, který je stále zbývající.</span><span class="sxs-lookup"><span data-stu-id="af345-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="af345-113">Důvod, proč je vlákno na tomto objektu blokováno.</span><span class="sxs-lookup"><span data-stu-id="af345-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af345-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af345-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af345-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af345-115">Requirements</span></span>  
 <span data-ttu-id="af345-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af345-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af345-117">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="af345-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="af345-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="af345-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af345-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af345-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af345-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af345-120">See also</span></span>

- [<span data-ttu-id="af345-121">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="af345-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="af345-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="af345-122">Debugging</span></span>](index.md)
