---
title: ICorDebugValue2::GetExactType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c28ff84b08802246d587bfa130ae5915177932ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764301"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="a5cf9-102">ICorDebugValue2::GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="a5cf9-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="a5cf9-103">Získá ukazatel rozhraní na objekt, který představuje "ICorDebugType" <xref:System.Type> z této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5cf9-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5cf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5cf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5cf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5cf9-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="a5cf9-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje <xref:System.Type> hodnoty reprezentovaný tímto objektem "icordebugvalue2 –".</span><span class="sxs-lookup"><span data-stu-id="a5cf9-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5cf9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5cf9-107">Remarks</span></span>  
 <span data-ttu-id="a5cf9-108">Obecné typy podporující `GetExactType` metoda nahrazuje i [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody, každý z které vrácené informace o typu hodnoty .</span><span class="sxs-lookup"><span data-stu-id="a5cf9-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5cf9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5cf9-109">Requirements</span></span>  
 <span data-ttu-id="a5cf9-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5cf9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5cf9-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5cf9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5cf9-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5cf9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5cf9-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5cf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cf9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5cf9-114">See also</span></span>
