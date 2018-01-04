---
title: "ICorDebugThread4::GetBlockingObjects – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006535885868ef2778146f86e5395ea1f7605d6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="8ce70-102">ICorDebugThread4::GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="8ce70-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="8ce70-103">Poskytuje seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vláken struktury, které poskytují informace o blokování.</span><span class="sxs-lookup"><span data-stu-id="8ce70-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ce70-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ce70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ce70-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8ce70-106">[out] Ukazatel na seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="8ce70-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce70-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ce70-107">Remarks</span></span>  
 <span data-ttu-id="8ce70-108">První element ve vráceném výčtu odpovídá na první strukturu, která blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="8ce70-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="8ce70-109">Druhý prvkem odpovídá blokování položku, která je došlo při spouštění volání asynchronní procedury (APC), pokud je blokováno v prvním a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8ce70-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="8ce70-110">Výčet je platný pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="8ce70-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="8ce70-111">Tato metoda musí být volána při ladění je ve stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="8ce70-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="8ce70-112">Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledkem nedefinovaný.</span><span class="sxs-lookup"><span data-stu-id="8ce70-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="8ce70-113">Pokud vlákno je blokovaný a nelze určit chyba, vrátí metoda HRESULT označující selhání; v opačném případě vrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="8ce70-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce70-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ce70-114">Requirements</span></span>  
 <span data-ttu-id="8ce70-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ce70-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce70-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ce70-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ce70-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce70-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce70-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce70-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce70-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ce70-119">See Also</span></span>  
 [<span data-ttu-id="8ce70-120">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ce70-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="8ce70-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8ce70-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8ce70-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="8ce70-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
