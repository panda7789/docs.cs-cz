---
title: COR_ACTIVE_FUNCTION – struktura
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274147"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="10539-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="10539-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="10539-103">Obsahuje informace o funkcích, které jsou aktuálně aktivní v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="10539-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="10539-104">Tato struktura je používána metodou [ICorDebugThread2:: GetActiveFunctions –](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="10539-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10539-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10539-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="10539-106">Členové</span><span class="sxs-lookup"><span data-stu-id="10539-106">Members</span></span>  
  
|<span data-ttu-id="10539-107">Člen</span><span class="sxs-lookup"><span data-stu-id="10539-107">Member</span></span>|<span data-ttu-id="10539-108">Popis</span><span class="sxs-lookup"><span data-stu-id="10539-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="10539-109">Ukazatel na vlastníka domény aplikace daného `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="10539-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="10539-110">Ukazatel na vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="10539-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="10539-111">Ukazatel na vlastníka `ilOffset` funkce pole.</span><span class="sxs-lookup"><span data-stu-id="10539-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="10539-112">Posun jazyka MSIL (Microsoft Intermediate Language) rámce.</span><span class="sxs-lookup"><span data-stu-id="10539-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="10539-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="10539-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10539-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10539-114">Requirements</span></span>  
 <span data-ttu-id="10539-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10539-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10539-116">**Hlaviček** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="10539-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="10539-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10539-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10539-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10539-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10539-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10539-119">See also</span></span>

- [<span data-ttu-id="10539-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="10539-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="10539-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="10539-121">Debugging</span></span>](index.md)
