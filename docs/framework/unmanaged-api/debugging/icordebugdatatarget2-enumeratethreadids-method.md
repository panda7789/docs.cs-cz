---
title: ICorDebugDataTarget2::EnumerateThreadIDs – metoda
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 74d4905f2b386f8e0345e4300dd2c8c6d0c882ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783643"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="cff53-102">ICorDebugDataTarget2::EnumerateThreadIDs – metoda</span><span class="sxs-lookup"><span data-stu-id="cff53-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="cff53-103">Vrátí seznam identifikátorů aktivních vláken.</span><span class="sxs-lookup"><span data-stu-id="cff53-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff53-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cff53-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cff53-105">Parameters</span></span>  
 <span data-ttu-id="cff53-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="cff53-106">cThreadIDs</span></span>  
 <span data-ttu-id="cff53-107">pro Maximální počet podprocesů, jejichž ID lze vrátit.</span><span class="sxs-lookup"><span data-stu-id="cff53-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="cff53-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="cff53-108">pcThreadIds</span></span>  
 <span data-ttu-id="cff53-109">mimo Ukazatel na `ULONG32`, který označuje skutečný počet ID vláken zapsaných do pole `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="cff53-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="cff53-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="cff53-110">pThreadIDs</span></span>  
 <span data-ttu-id="cff53-111">Pole identifikátorů vláken.</span><span class="sxs-lookup"><span data-stu-id="cff53-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff53-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cff53-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cff53-113">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cff53-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff53-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cff53-114">Requirements</span></span>  
 <span data-ttu-id="cff53-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md). **Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cff53-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cff53-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cff53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff53-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff53-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff53-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cff53-118">See also</span></span>

- [<span data-ttu-id="cff53-119">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cff53-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="cff53-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cff53-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
