---
title: ICorDebugDataTarget2::EnumerateThreadIDs – metoda
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 120a970aac33b1ab06ae47335a959d2791f893ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178981"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="de6f6-102">ICorDebugDataTarget2::EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="de6f6-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="de6f6-103">Vrátí seznam aktivních ID vláken.</span><span class="sxs-lookup"><span data-stu-id="de6f6-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de6f6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de6f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de6f6-105">Parameters</span></span>  
 <span data-ttu-id="de6f6-106">cID vláken</span><span class="sxs-lookup"><span data-stu-id="de6f6-106">cThreadIDs</span></span>  
 <span data-ttu-id="de6f6-107">[v] Maximální počet podprocesů, jejichž ID mohou být vráceny.</span><span class="sxs-lookup"><span data-stu-id="de6f6-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="de6f6-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="de6f6-108">pcThreadIds</span></span>  
 <span data-ttu-id="de6f6-109">[out] Ukazatel na `ULONG32` a, který označuje skutečný počet ID `pThreadIds` podprocesů zapsaných do pole.</span><span class="sxs-lookup"><span data-stu-id="de6f6-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="de6f6-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="de6f6-110">pThreadIDs</span></span>  
 <span data-ttu-id="de6f6-111">Pole identifikátorů vláken.</span><span class="sxs-lookup"><span data-stu-id="de6f6-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de6f6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de6f6-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de6f6-113">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="de6f6-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6f6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de6f6-114">Requirements</span></span>  
 <span data-ttu-id="de6f6-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md). **Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de6f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de6f6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de6f6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de6f6-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6f6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6f6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="de6f6-118">See also</span></span>

- [<span data-ttu-id="de6f6-119">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6f6-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="de6f6-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6f6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
