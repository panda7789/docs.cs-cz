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
ms.openlocfilehash: 8a6e4f6e7e3107516476b179b0ed718ca44bb114
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103389"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="b56a9-102">ICorDebugCode4::EnumerateVariableHomes – metoda</span><span class="sxs-lookup"><span data-stu-id="b56a9-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="b56a9-103">Získá enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b56a9-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b56a9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b56a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b56a9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b56a9-106">Ukazatel na adresu [icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní objektu, který je enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b56a9-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b56a9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b56a9-107">Remarks</span></span>  
 <span data-ttu-id="b56a9-108">[Icordebugvariablehomeenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objektu rozhraní je standardní enumerátor odvozen z rozhraní "ICorDebugEnum", který umožňuje vytvořit výčet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="b56a9-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="b56a9-109">Kolekce může zahrnovat více [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objekty pro stejný index pozice nebo argument, pokud mají různé domovů v různých fázích funkce.</span><span class="sxs-lookup"><span data-stu-id="b56a9-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b56a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b56a9-110">Requirements</span></span>  
 <span data-ttu-id="b56a9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b56a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b56a9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b56a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b56a9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b56a9-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b56a9-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b56a9-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b56a9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b56a9-115">See also</span></span>

- [<span data-ttu-id="b56a9-116">ICorDebugCode4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b56a9-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="b56a9-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b56a9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
