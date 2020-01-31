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
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792378"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="66216-102">ICorDebugProcess5::GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="66216-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="66216-103">Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, jestli je aktuálně vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="66216-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66216-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66216-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66216-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66216-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="66216-106">mimo Ukazatel na hodnotu [COR_HEAPINFO](cor-heapinfo-structure.md) , která poskytuje obecné informace o haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="66216-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66216-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66216-107">Remarks</span></span>  
 <span data-ttu-id="66216-108">Aby bylo zajištěno, že struktury uvolňování paměti v procesu jsou aktuálně platné, je nutné volat metodu `ICorDebugProcess5::GetGCHeapInformation`.</span><span class="sxs-lookup"><span data-stu-id="66216-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="66216-109">V průběhu shromažďování nelze vás provedl haldu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="66216-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="66216-110">Jinak výčet může zachytit struktury uvolňování paměti, které jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="66216-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66216-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66216-111">Requirements</span></span>  
 <span data-ttu-id="66216-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66216-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66216-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66216-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66216-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66216-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66216-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66216-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66216-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66216-116">See also</span></span>

- [<span data-ttu-id="66216-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66216-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="66216-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="66216-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
