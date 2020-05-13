---
title: ICorDebugProcess5::GetGCHeapInformation – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 62d45da44a95eae399fbbd287aa997a5f913d0b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209653"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="95404-102">ICorDebugProcess5::GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="95404-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="95404-103">Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, jestli je aktuálně vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="95404-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95404-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95404-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95404-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95404-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="95404-106">mimo Ukazatel na hodnotu [COR_HEAPINFO](cor-heapinfo-structure.md) , která poskytuje obecné informace o haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="95404-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95404-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95404-107">Remarks</span></span>  
 <span data-ttu-id="95404-108">`ICorDebugProcess5::GetGCHeapInformation`Metoda musí být volána před vytvořením výčtu oblasti haldy nebo jednotlivých oblastí haldy, aby bylo zajištěno, že struktury uvolňování paměti v procesu jsou aktuálně platné.</span><span class="sxs-lookup"><span data-stu-id="95404-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="95404-109">V průběhu shromažďování nelze vás provedl haldu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="95404-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="95404-110">Jinak výčet může zachytit struktury uvolňování paměti, které jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="95404-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95404-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95404-111">Requirements</span></span>  
 <span data-ttu-id="95404-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95404-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95404-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95404-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95404-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="95404-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95404-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95404-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95404-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="95404-116">See also</span></span>

- [<span data-ttu-id="95404-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95404-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="95404-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95404-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
