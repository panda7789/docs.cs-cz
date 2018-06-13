---
title: ICorDebugDataTarget2::EnumerateThreadIDs – metoda
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d915c7d5521e630602f4dac6c905920fd2fab9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411444"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="5525b-102">ICorDebugDataTarget2::EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="5525b-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="5525b-103">Vrátí seznam aktivních vláken ID.</span><span class="sxs-lookup"><span data-stu-id="5525b-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5525b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5525b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5525b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5525b-105">Parameters</span></span>  
 <span data-ttu-id="5525b-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="5525b-106">cThreadIDs</span></span>  
 <span data-ttu-id="5525b-107">[v] Maximální počet vláken, jehož ID se může vracet.</span><span class="sxs-lookup"><span data-stu-id="5525b-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="5525b-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="5525b-108">pcThreadIds</span></span>  
 <span data-ttu-id="5525b-109">[out] Ukazatel `ULONG32` určující, skutečný počet vláken ID zapsána do `pThreadIds` pole.</span><span class="sxs-lookup"><span data-stu-id="5525b-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="5525b-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="5525b-110">pThreadIDs</span></span>  
 <span data-ttu-id="5525b-111">Pole identifikátory přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="5525b-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5525b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5525b-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5525b-113">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="5525b-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5525b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5525b-114">Requirements</span></span>  
 <span data-ttu-id="5525b-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md). **Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5525b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5525b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5525b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5525b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5525b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5525b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5525b-118">See Also</span></span>  
 [<span data-ttu-id="5525b-119">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5525b-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="5525b-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5525b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
