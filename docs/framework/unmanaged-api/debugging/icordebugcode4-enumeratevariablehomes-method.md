---
title: ICorDebugCode4::EnumerateVariableHomes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e6acdf6996f437c85b629b0af886287b1aef03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748555"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="ce00a-102">ICorDebugCode4::EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="ce00a-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="ce00a-103">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="ce00a-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce00a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce00a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce00a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce00a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ce00a-106">Ukazatel na adresu [icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní objektu, který je enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="ce00a-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce00a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce00a-107">Remarks</span></span>  
 <span data-ttu-id="ce00a-108">[Icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objektu rozhraní je standardní enumerátor odvozen z rozhraní "ICorDebugEnum", který umožňuje vytvořit výčet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="ce00a-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="ce00a-109">Kolekce může zahrnovat více [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty pro stejný index pozice nebo argument, pokud mají různé domovů v různých fázích funkce.</span><span class="sxs-lookup"><span data-stu-id="ce00a-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce00a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce00a-110">Requirements</span></span>  
 <span data-ttu-id="ce00a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce00a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce00a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce00a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce00a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce00a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce00a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce00a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce00a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce00a-115">See also</span></span>

- [<span data-ttu-id="ce00a-116">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce00a-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="ce00a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ce00a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
