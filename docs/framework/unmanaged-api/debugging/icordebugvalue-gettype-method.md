---
title: "ICorDebugValue::GetType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a79ef332361fdaa3a23cc4e13daa8b4a8303d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="47b05-102">ICorDebugValue::GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="47b05-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="47b05-103">Získá primitivní typ tohoto objektu "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="47b05-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47b05-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47b05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47b05-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="47b05-106">[out] Ukazatel na hodnotu "CorElementType" výčtu, která určuje typ hodnotu.</span><span class="sxs-lookup"><span data-stu-id="47b05-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47b05-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47b05-107">Remarks</span></span>  
 <span data-ttu-id="47b05-108">Pokud se objekt komplexní typ spuštění, typu může zkoumány prostřednictvím příslušné měly podtřídy `ICorDebugValue` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47b05-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="47b05-109">Například "ICorDebugObjectValue", který dědí z `ICorDebugValue`, představuje komplexního typu.</span><span class="sxs-lookup"><span data-stu-id="47b05-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="47b05-110">`GetType` a [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) každá z metod vrácení informací o typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="47b05-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="47b05-111">Obě jsou nahrazeny touto obecné typy podporující [icordebugvalue2::getexacttype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="47b05-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b05-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47b05-112">Requirements</span></span>  
 <span data-ttu-id="47b05-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47b05-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47b05-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47b05-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47b05-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47b05-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47b05-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47b05-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b05-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="47b05-117">See Also</span></span>  
 
