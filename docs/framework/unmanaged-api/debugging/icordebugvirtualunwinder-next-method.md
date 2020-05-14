---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396427"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="e60fc-102">ICorDebugVirtualUnwinder:: Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e60fc-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="e60fc-103">Přejde do kontextu volajícího.</span><span class="sxs-lookup"><span data-stu-id="e60fc-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e60fc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="e60fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e60fc-105">Parameters</span></span>  
 <span data-ttu-id="e60fc-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="e60fc-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e60fc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e60fc-107">Return Value</span></span>  
 <span data-ttu-id="e60fc-108">`S_OK`Pokud se unwind úspěšně nastalo, nebo `CORDBG_S_AT_END_OF_STACK` Pokud se unwind nedá dokončit, protože neexistují žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="e60fc-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="e60fc-109">Pokud se vrátí neúspěšná hodnota HRESULT, vrátí rozhraní API ICorDebug `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="e60fc-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e60fc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e60fc-110">Remarks</span></span>  
 <span data-ttu-id="e60fc-111">Zásobník prohlížeč by měl zajistit, že předává průběh vpřed, takže nakonec volání `Next` vrátí HRESULT nebo `CORDBG_S_AT_END_OF_STACK` .</span><span class="sxs-lookup"><span data-stu-id="e60fc-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="e60fc-112">Vrácení bez `S_OK` omezení může způsobit nekonečnou smyčku.</span><span class="sxs-lookup"><span data-stu-id="e60fc-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e60fc-113">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e60fc-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e60fc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e60fc-114">Requirements</span></span>  
 <span data-ttu-id="e60fc-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e60fc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e60fc-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e60fc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e60fc-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e60fc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e60fc-118">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e60fc-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60fc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e60fc-119">See also</span></span>

- [<span data-ttu-id="e60fc-120">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e60fc-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="e60fc-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e60fc-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
