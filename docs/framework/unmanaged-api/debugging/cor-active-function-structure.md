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
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132386"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="270b1-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="270b1-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="270b1-103">Obsahuje informace o funkcích, které jsou aktuálně aktivní v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="270b1-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="270b1-104">Tato struktura je používána metodou [ICorDebugThread2:: GetActiveFunctions –](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="270b1-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="270b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="270b1-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="270b1-106">Členové</span><span class="sxs-lookup"><span data-stu-id="270b1-106">Members</span></span>  
  
|<span data-ttu-id="270b1-107">Člen</span><span class="sxs-lookup"><span data-stu-id="270b1-107">Member</span></span>|<span data-ttu-id="270b1-108">Popis</span><span class="sxs-lookup"><span data-stu-id="270b1-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="270b1-109">Ukazatel na vlastníka domény aplikace v poli `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="270b1-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="270b1-110">Ukazatel na vlastníka modulu pole `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="270b1-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="270b1-111">Ukazatel na vlastníka funkce pole `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="270b1-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="270b1-112">Posun jazyka MSIL (Microsoft Intermediate Language) rámce.</span><span class="sxs-lookup"><span data-stu-id="270b1-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="270b1-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="270b1-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="270b1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="270b1-114">Requirements</span></span>  
 <span data-ttu-id="270b1-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="270b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="270b1-116">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="270b1-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="270b1-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="270b1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="270b1-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="270b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270b1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="270b1-119">See also</span></span>

- [<span data-ttu-id="270b1-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="270b1-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="270b1-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="270b1-121">Debugging</span></span>](index.md)
