---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7325e84d8fe4df9a31543426c6376d0941306fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748453"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="d1433-102">ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="d1433-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="d1433-103">Poskytuje enumerátor pro typy rozhraní, že byl přetypován na nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="d1433-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1433-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1433-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1433-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="d1433-106">[in] Hodnota, která určuje, zda metoda vrátí pouze rozhraní Windows Runtime (`IInspectable` rozhraní) nebo jen rozhraní modelu COM v mezipaměti obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="d1433-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="d1433-107">[out] Ukazatel na adresu, která poskytuje přístup k objektům ICorDebugType, které představují typy z mezipaměti rozhraní čítače icordebugtypeenum – filtrovat podle `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="d1433-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1433-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1433-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1433-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1433-109">Requirements</span></span>  
 <span data-ttu-id="d1433-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1433-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1433-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1433-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1433-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1433-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1433-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1433-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1433-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1433-114">See also</span></span>

- [<span data-ttu-id="d1433-115">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1433-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d1433-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d1433-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
