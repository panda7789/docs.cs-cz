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
ms.openlocfilehash: e4d5582b7a3df16db58ea0ed001dcbffcdcaab79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122452"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="74396-102">ICorDebugThread4::GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="74396-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="74396-103">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="74396-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74396-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74396-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="74396-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74396-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="74396-106">mimo Ukazatel na seřazený výčet struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="74396-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74396-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74396-107">Remarks</span></span>  
 <span data-ttu-id="74396-108">První prvek vráceného výčtu odpovídá první struktuře, která blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="74396-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="74396-109">Druhý prvek odpovídá blokující položce, která se objevila při spuštění asynchronní procedury volání (APC) při zablokování v prvním, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="74396-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="74396-110">Výčet je platný pouze po dobu trvání aktuálního synchronizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="74396-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="74396-111">Tato metoda musí být volána, když je laděného procesu v synchronizovaném stavu.</span><span class="sxs-lookup"><span data-stu-id="74396-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="74396-112">Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="74396-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="74396-113">Pokud je vlákno blokované a chybu nelze určit, metoda vrátí hodnotu HRESULT, která označuje selhání. v opačném případě vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="74396-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74396-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74396-114">Requirements</span></span>  
 <span data-ttu-id="74396-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74396-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74396-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74396-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74396-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74396-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74396-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74396-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74396-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74396-119">See also</span></span>

- [<span data-ttu-id="74396-120">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74396-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="74396-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="74396-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="74396-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="74396-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
