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
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791378"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="e23a2-102">ICorDebugThread4::GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="e23a2-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="e23a2-103">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="e23a2-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e23a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="e23a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e23a2-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="e23a2-106">mimo Ukazatel na seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e23a2-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e23a2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e23a2-107">Remarks</span></span>  
 <span data-ttu-id="e23a2-108">První prvek vráceného výčtu odpovídá první struktuře, která blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="e23a2-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="e23a2-109">Druhý prvek odpovídá blokující položce, která se objevila při spuštění asynchronní procedury volání (APC) při zablokování v prvním, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e23a2-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="e23a2-110">Výčet je platný pouze po dobu trvání aktuálního synchronizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="e23a2-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="e23a2-111">Tato metoda musí být volána, když je laděného procesu v synchronizovaném stavu.</span><span class="sxs-lookup"><span data-stu-id="e23a2-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="e23a2-112">Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="e23a2-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="e23a2-113">Pokud je vlákno blokované a chybu nelze určit, metoda vrátí hodnotu HRESULT, která označuje selhání. v opačném případě vrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="e23a2-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23a2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e23a2-114">Requirements</span></span>  
 <span data-ttu-id="e23a2-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e23a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23a2-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e23a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e23a2-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e23a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e23a2-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e23a2-119">See also</span></span>

- [<span data-ttu-id="e23a2-120">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23a2-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="e23a2-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e23a2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e23a2-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="e23a2-122">Debugging</span></span>](index.md)
