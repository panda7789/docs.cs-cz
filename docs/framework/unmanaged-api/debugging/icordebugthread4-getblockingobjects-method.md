---
title: ICorDebugThread4::GetBlockingObjects – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93cae803b42d80dc0f868e2189de442eedea43f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993873"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="f9220-102">ICorDebugThread4::GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="f9220-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="f9220-103">Poskytuje seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vlákna struktury, které poskytují informace o blokování.</span><span class="sxs-lookup"><span data-stu-id="f9220-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9220-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9220-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9220-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="f9220-106">[out] Ukazatel na seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="f9220-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9220-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9220-107">Remarks</span></span>  
 <span data-ttu-id="f9220-108">První prvek ve vrácené výčtu odpovídá první strukturu, která blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="f9220-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="f9220-109">Druhý prvek odpovídá blokující položkou, na kterou narazí při spouštění volání rozhraní asynchronní procedury (APC) při zablokování prvního a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f9220-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="f9220-110">Výčet je platný pouze po dobu trvání aktuálního stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="f9220-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="f9220-111">Tato metoda musí být volána, když laděný proces je ve stavu synchronizovaná.</span><span class="sxs-lookup"><span data-stu-id="f9220-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="f9220-112">Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek nedefinován.</span><span class="sxs-lookup"><span data-stu-id="f9220-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="f9220-113">Pokud je vlákno blokované a chyba nelze určit, že vrátí tato metoda hodnotu HRESULT označující selhání; v opačném případě vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="f9220-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9220-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9220-114">Requirements</span></span>  
 <span data-ttu-id="f9220-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9220-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9220-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9220-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9220-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9220-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9220-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9220-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9220-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9220-119">See also</span></span>

- [<span data-ttu-id="f9220-120">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9220-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="f9220-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f9220-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f9220-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="f9220-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
