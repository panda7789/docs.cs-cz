---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 387dc484b3ada63d62ddc27318e735dfc4ea93b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492267"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="77cf0-102">ICorDebugDataTarget2::CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="77cf0-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="77cf0-103">Vytvoří nový unwinder zásobníku, který se spustí uvolnění z počáteční kontextu, (což není nutně listu vlákno).</span><span class="sxs-lookup"><span data-stu-id="77cf0-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77cf0-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="77cf0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77cf0-105">Parameters</span></span>  
 <span data-ttu-id="77cf0-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="77cf0-106">nativeThreadID</span></span>  
 <span data-ttu-id="77cf0-107">[in] ID nativní vlákna vlákna, jehož zásobník má být oddělen.</span><span class="sxs-lookup"><span data-stu-id="77cf0-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="77cf0-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="77cf0-108">contextFlags</span></span>  
 <span data-ttu-id="77cf0-109">[in] Příznaky, které určují, které části kontextu jsou definovány v `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="77cf0-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="77cf0-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="77cf0-110">cbContext</span></span>  
 <span data-ttu-id="77cf0-111">[in] Velikost `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="77cf0-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="77cf0-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="77cf0-112">initialContext</span></span>  
 <span data-ttu-id="77cf0-113">[in] Data v kontextu.</span><span class="sxs-lookup"><span data-stu-id="77cf0-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="77cf0-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="77cf0-114">ppUnwinder</span></span>  
 <span data-ttu-id="77cf0-115">[out] Ukazatel na adresu objektu rozhraní ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="77cf0-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77cf0-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="77cf0-116">Return Value</span></span>  
 <span data-ttu-id="77cf0-117">`S_OK` v případě úspěšného ověření.</span><span class="sxs-lookup"><span data-stu-id="77cf0-117">`S_OK` if successful.</span></span> <span data-ttu-id="77cf0-118">Jakýkoli jiný `HRESULT` označuje chybu.</span><span class="sxs-lookup"><span data-stu-id="77cf0-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="77cf0-119">Všechny neúspěšné `HRESULT` přijatých mscordbi se považuje za závažné a způsobí, že [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody k vrácení `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="77cf0-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77cf0-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77cf0-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77cf0-121">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77cf0-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77cf0-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77cf0-122">Requirements</span></span>  
 <span data-ttu-id="77cf0-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77cf0-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77cf0-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77cf0-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77cf0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77cf0-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77cf0-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cf0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77cf0-127">See also</span></span>
- [<span data-ttu-id="77cf0-128">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77cf0-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="77cf0-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="77cf0-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
