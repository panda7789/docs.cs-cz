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
ms.openlocfilehash: 6b02657012870de4d0f888f6c05b115b25073fa2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892836"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="214be-102">ICorDebugComObjectValue::GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="214be-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="214be-103">Poskytuje enumerátor pro typy rozhraní, na které byl aktuální objekt převeden nebo použit jako.</span><span class="sxs-lookup"><span data-stu-id="214be-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="214be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="214be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="214be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="214be-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="214be-106">pro Hodnota, která určuje, zda metoda vrátí pouze prostředí Windows Runtime rozhraní (`IInspectable` rozhraní) nebo všechna rozhraní COM uložená v mezipaměti pomocí obálky volání za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="214be-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="214be-107">mimo Ukazatel na adresu čítače výčtu ICorDebugTypeEnum, který poskytuje přístup k objektům ICorDebugType, které představují typy rozhraní uložené v mezipaměti, `bIInspectableOnly`které jsou filtrovány podle.</span><span class="sxs-lookup"><span data-stu-id="214be-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="214be-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="214be-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="214be-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="214be-109">Requirements</span></span>  
 <span data-ttu-id="214be-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="214be-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="214be-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="214be-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="214be-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="214be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="214be-113">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="214be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214be-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="214be-114">See also</span></span>

- [<span data-ttu-id="214be-115">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="214be-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="214be-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="214be-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
