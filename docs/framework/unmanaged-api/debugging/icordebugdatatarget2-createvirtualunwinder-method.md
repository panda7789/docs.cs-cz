---
title: ICorDebugDataTarget2::CreateVirtualUnwinder – metoda
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 7a479fba9bbcf28c60474fffc6219af23e62c251
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976496"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="96d33-102">ICorDebugDataTarget2::CreateVirtualUnwinder – metoda</span><span class="sxs-lookup"><span data-stu-id="96d33-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="96d33-103">Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).</span><span class="sxs-lookup"><span data-stu-id="96d33-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96d33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96d33-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="96d33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96d33-105">Parameters</span></span>  
 <span data-ttu-id="96d33-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="96d33-106">nativeThreadID</span></span>  
 <span data-ttu-id="96d33-107">pro ID nativního vlákna vlákna, jehož zásobník má být oddělitelné.</span><span class="sxs-lookup"><span data-stu-id="96d33-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="96d33-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="96d33-108">contextFlags</span></span>  
 <span data-ttu-id="96d33-109">pro Příznaky, které určují, které části kontextu jsou definovány v `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="96d33-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="96d33-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="96d33-110">cbContext</span></span>  
 <span data-ttu-id="96d33-111">pro Velikost `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="96d33-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="96d33-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="96d33-112">initialContext</span></span>  
 <span data-ttu-id="96d33-113">pro Data v kontextu.</span><span class="sxs-lookup"><span data-stu-id="96d33-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="96d33-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="96d33-114">ppUnwinder</span></span>  
 <span data-ttu-id="96d33-115">mimo Ukazatel na adresu objektu rozhraní ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="96d33-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96d33-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96d33-116">Return Value</span></span>  
 <span data-ttu-id="96d33-117">`S_OK`v případě úspěchu.</span><span class="sxs-lookup"><span data-stu-id="96d33-117">`S_OK` if successful.</span></span> <span data-ttu-id="96d33-118">Jakýkoli jiný `HRESULT` indikuje selhání.</span><span class="sxs-lookup"><span data-stu-id="96d33-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="96d33-119">Jakékoli selhání `HRESULT` přijaté službou mscordbi se považuje za závažné a způsobí, že [ICorDebug](icordebug-interface.md) metody vrátí `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="96d33-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96d33-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96d33-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96d33-121">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96d33-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96d33-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96d33-122">Requirements</span></span>  
 <span data-ttu-id="96d33-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d33-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96d33-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96d33-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96d33-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96d33-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96d33-126">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96d33-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d33-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="96d33-127">See also</span></span>

- [<span data-ttu-id="96d33-128">Rozhraní ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="96d33-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="96d33-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96d33-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
