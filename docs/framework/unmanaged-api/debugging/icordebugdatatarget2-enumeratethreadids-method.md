---
title: ICorDebugDataTarget2::EnumerateThreadIDs – metoda
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 594fcb74988cadaa4801fc6f0bb2d05b27a7f441
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563389"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="659cc-102">ICorDebugDataTarget2::EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="659cc-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="659cc-103">Vrátí seznam hodnot aktivní vlákno ID.</span><span class="sxs-lookup"><span data-stu-id="659cc-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="659cc-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="659cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="659cc-105">Parameters</span></span>  
 <span data-ttu-id="659cc-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="659cc-106">cThreadIDs</span></span>  
 <span data-ttu-id="659cc-107">[in] Maximální počet vláken, jejichž ID může být vrácen.</span><span class="sxs-lookup"><span data-stu-id="659cc-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="659cc-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="659cc-108">pcThreadIds</span></span>  
 <span data-ttu-id="659cc-109">[out] Ukazatel `ULONG32` , která indikuje, skutečný počet vláken ID zapsána do `pThreadIds` pole.</span><span class="sxs-lookup"><span data-stu-id="659cc-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="659cc-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="659cc-110">pThreadIDs</span></span>  
 <span data-ttu-id="659cc-111">Pole identifikátory vlákna.</span><span class="sxs-lookup"><span data-stu-id="659cc-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="659cc-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="659cc-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="659cc-113">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="659cc-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="659cc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="659cc-114">Requirements</span></span>  
 <span data-ttu-id="659cc-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md). **Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="659cc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="659cc-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="659cc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="659cc-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="659cc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659cc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="659cc-118">See also</span></span>
- [<span data-ttu-id="659cc-119">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="659cc-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="659cc-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="659cc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
