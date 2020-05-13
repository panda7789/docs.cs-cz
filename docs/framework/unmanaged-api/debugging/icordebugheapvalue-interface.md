---
title: ICorDebugHeapValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213007"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="a8a67-102">ICorDebugHeapValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8a67-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="a8a67-103">Podtřída "ICorDebugValue", která představuje objekt, který byl shromážděn systémem uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a8a67-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8a67-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a8a67-104">Methods</span></span>  
  
|<span data-ttu-id="a8a67-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a8a67-105">Method</span></span>|<span data-ttu-id="a8a67-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a8a67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8a67-107">CreateRelocBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="a8a67-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="a8a67-108">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="a8a67-108">Not implemented.</span></span>|  
|[<span data-ttu-id="a8a67-109">IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="a8a67-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="a8a67-110">Získá hodnotu, která označuje, zda je objekt reprezentovaný tímto argumentem `ICorDebugHeapValue` platný, nebo byl uvolněn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a8a67-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="a8a67-111">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a8a67-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8a67-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8a67-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8a67-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a8a67-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a67-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8a67-114">Requirements</span></span>  
 <span data-ttu-id="a8a67-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a67-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a67-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8a67-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8a67-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8a67-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8a67-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a67-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a67-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8a67-119">See also</span></span>

- [<span data-ttu-id="a8a67-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8a67-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
