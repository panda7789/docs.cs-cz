---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788853"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="89238-102">ICorDebugDataTarget2::CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="89238-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="89238-103">Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).</span><span class="sxs-lookup"><span data-stu-id="89238-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89238-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="89238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89238-105">Parameters</span></span>  
 <span data-ttu-id="89238-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="89238-106">nativeThreadID</span></span>  
 <span data-ttu-id="89238-107">pro ID nativního vlákna vlákna, jehož zásobník má být oddělitelné.</span><span class="sxs-lookup"><span data-stu-id="89238-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="89238-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="89238-108">contextFlags</span></span>  
 <span data-ttu-id="89238-109">pro Příznaky, které určují, které části kontextu jsou definovány v `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="89238-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="89238-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="89238-110">cbContext</span></span>  
 <span data-ttu-id="89238-111">pro Velikost `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="89238-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="89238-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="89238-112">initialContext</span></span>  
 <span data-ttu-id="89238-113">pro Data v kontextu.</span><span class="sxs-lookup"><span data-stu-id="89238-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="89238-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="89238-114">ppUnwinder</span></span>  
 <span data-ttu-id="89238-115">mimo Ukazatel na adresu objektu rozhraní ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="89238-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89238-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89238-116">Return Value</span></span>  
 <span data-ttu-id="89238-117">`S_OK`, pokud bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="89238-117">`S_OK` if successful.</span></span> <span data-ttu-id="89238-118">Všechny ostatní `HRESULT` označují selhání.</span><span class="sxs-lookup"><span data-stu-id="89238-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="89238-119">Jakákoli neúspěšná `HRESULT` přijatá nástrojem mscordbi se považuje za závažnou a způsobí, že metody [ICorDebug](icordebug-interface.md) vrátí `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="89238-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89238-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89238-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89238-121">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="89238-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89238-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89238-122">Requirements</span></span>  
 <span data-ttu-id="89238-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89238-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89238-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89238-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89238-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89238-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89238-126">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89238-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89238-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89238-127">See also</span></span>

- [<span data-ttu-id="89238-128">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89238-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="89238-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="89238-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
