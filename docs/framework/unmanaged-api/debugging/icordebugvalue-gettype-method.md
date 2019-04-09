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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83265c4f6dffed76f1710378cf5293aac7020ef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119350"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="5f8fe-102">ICorDebugValue::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="5f8fe-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="5f8fe-103">Získá základní typ tohoto objektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="5f8fe-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f8fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f8fe-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f8fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f8fe-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="5f8fe-106">[out] Ukazatel na hodnotu "Corelementtype –" výčtu, která určuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f8fe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f8fe-107">Remarks</span></span>  
 <span data-ttu-id="5f8fe-108">Pokud se objekt komplexního typu za běhu, tento typ se můžou zkoumat prostřednictvím odpovídající podtřídy třídy `ICorDebugValue` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="5f8fe-109">Například "ICorDebugObjectValue", která dědí z `ICorDebugValue`, představuje komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="5f8fe-110">`GetType` a [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) každá z metod vrací informace o typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="5f8fe-111">Jsou obě nahrazeny obecných typů podporujících [icordebugvalue2::getexacttype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5f8fe-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f8fe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f8fe-112">Requirements</span></span>  
 <span data-ttu-id="5f8fe-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f8fe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f8fe-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f8fe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f8fe-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f8fe-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5f8fe-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5f8fe-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f8fe-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f8fe-117">See also</span></span>
