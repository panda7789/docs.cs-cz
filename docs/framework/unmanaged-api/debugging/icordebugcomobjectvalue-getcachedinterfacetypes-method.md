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
ms.openlocfilehash: 36e6313ae7b4c67a20bee6d2a76a4ed1da84acbe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115216"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="2132f-102">ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="2132f-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="2132f-103">Poskytuje enumerátor pro typy rozhraní, že byl přetypován na nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="2132f-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2132f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2132f-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2132f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2132f-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="2132f-106">[in] Hodnota, která určuje, zda metoda vrátí pouze [!INCLUDE[wrt](../../../../includes/wrt-md.md)] rozhraní (`IInspectable` rozhraní) nebo jen rozhraní modelu COM v mezipaměti obálka volatelná za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="2132f-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="2132f-107">[out] Ukazatel na adresu, která poskytuje přístup k objektům ICorDebugType, které představují typy z mezipaměti rozhraní čítače icordebugtypeenum – filtrovat podle `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="2132f-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2132f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2132f-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2132f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2132f-109">Requirements</span></span>  
 <span data-ttu-id="2132f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2132f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2132f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2132f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2132f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2132f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2132f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2132f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2132f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2132f-114">See also</span></span>

- [<span data-ttu-id="2132f-115">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2132f-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="2132f-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2132f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
