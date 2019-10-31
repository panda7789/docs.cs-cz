---
title: ICorDebugValue::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 284a74823b01305f8c6e025f70bb9209c8607b7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137077"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="256d9-102">ICorDebugValue::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="256d9-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="256d9-103">Získá primitivní typ tohoto objektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="256d9-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="256d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="256d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="256d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="256d9-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="256d9-106">mimo Ukazatel na hodnotu výčtu "CorElementType –", která označuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="256d9-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="256d9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="256d9-107">Remarks</span></span>  
 <span data-ttu-id="256d9-108">Pokud je objekt složitým typem běhu, lze tento typ prozkoumat pomocí příslušných podtříd `ICorDebugValue` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="256d9-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="256d9-109">Například "ICorDebugObjectValue", který dědí z `ICorDebugValue`představuje komplexní typ.</span><span class="sxs-lookup"><span data-stu-id="256d9-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="256d9-110">Metody `GetType` a [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) každou vrací informace o typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="256d9-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="256d9-111">Jsou obě nahrazeny metodou [ICorDebugValue2:: GetExactType –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) , která se s ohledem na obecné typy nahrazují.</span><span class="sxs-lookup"><span data-stu-id="256d9-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="256d9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="256d9-112">Requirements</span></span>  
 <span data-ttu-id="256d9-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="256d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="256d9-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="256d9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="256d9-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="256d9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="256d9-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="256d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="256d9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="256d9-117">See also</span></span>
