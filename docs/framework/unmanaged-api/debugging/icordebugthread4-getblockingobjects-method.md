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
ms.openlocfilehash: 366b5124cc66a4e9a1c3bd4e77f604f15ba8d8a8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379676"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="eed7b-102">ICorDebugThread4::GetBlockingObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="eed7b-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="eed7b-103">Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.</span><span class="sxs-lookup"><span data-stu-id="eed7b-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eed7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="eed7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eed7b-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="eed7b-106">mimo Ukazatel na seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="eed7b-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed7b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eed7b-107">Remarks</span></span>  
 <span data-ttu-id="eed7b-108">První prvek vráceného výčtu odpovídá první struktuře, která blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="eed7b-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="eed7b-109">Druhý prvek odpovídá blokující položce, která se objevila při spuštění asynchronní procedury volání (APC) při zablokování v prvním, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="eed7b-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="eed7b-110">Výčet je platný pouze po dobu trvání aktuálního synchronizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="eed7b-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="eed7b-111">Tato metoda musí být volána, když je laděného procesu v synchronizovaném stavu.</span><span class="sxs-lookup"><span data-stu-id="eed7b-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="eed7b-112">Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="eed7b-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="eed7b-113">Pokud je vlákno blokované a chybu nelze určit, metoda vrátí hodnotu HRESULT, která označuje selhání. v opačném případě vrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="eed7b-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed7b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eed7b-114">Requirements</span></span>  
 <span data-ttu-id="eed7b-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eed7b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed7b-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eed7b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eed7b-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="eed7b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eed7b-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed7b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed7b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="eed7b-119">See also</span></span>

- [<span data-ttu-id="eed7b-120">ICorDebugThread4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eed7b-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="eed7b-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eed7b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="eed7b-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="eed7b-122">Debugging</span></span>](index.md)
