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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8824ce004cac8bc2ad675c83dc6b5f167f183e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421044"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="5d26c-102">ICorDebugProcess5::GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="5d26c-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="5d26c-103">Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je aktuálně vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="5d26c-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d26c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d26c-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d26c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d26c-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="5d26c-106">[out] Ukazatel [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) hodnotu, která poskytuje obecné informace o kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="5d26c-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d26c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d26c-107">Remarks</span></span>  
 <span data-ttu-id="5d26c-108">`ICorDebugProcess5::GetGCHeapInformation` Před vytváření výčtu halda musí být volána metoda nebo jednotlivé haldy oblasti zajistit, že kolekce paměti struktur v procesu jsou aktuálně platná.</span><span class="sxs-lookup"><span data-stu-id="5d26c-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="5d26c-109">Kolekce halda paměti nelze proveden vaši firmu, když probíhá kolekce.</span><span class="sxs-lookup"><span data-stu-id="5d26c-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="5d26c-110">Jinak hodnota výčtu může zachytit struktury kolekce paměti, které jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="5d26c-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d26c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d26c-111">Requirements</span></span>  
 <span data-ttu-id="5d26c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d26c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d26c-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d26c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d26c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d26c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d26c-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d26c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d26c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d26c-116">See Also</span></span>  
 [<span data-ttu-id="5d26c-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d26c-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="5d26c-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5d26c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
