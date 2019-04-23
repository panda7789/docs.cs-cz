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
ms.openlocfilehash: 002e53d380140a63297a90baa270b5a6f1e5e328
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192261"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="10197-102">ICorDebugValue2::GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="10197-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="10197-103">Získá ukazatel rozhraní na objekt, který představuje "ICorDebugType" <xref:System.Type> z této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="10197-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10197-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10197-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10197-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10197-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="10197-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje <xref:System.Type> hodnoty reprezentovaný tímto objektem "icordebugvalue2 –".</span><span class="sxs-lookup"><span data-stu-id="10197-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10197-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10197-107">Remarks</span></span>  
 <span data-ttu-id="10197-108">Obecné typy podporující `GetExactType` metoda nahrazuje i [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody, každý z které vrácené informace o typu hodnoty .</span><span class="sxs-lookup"><span data-stu-id="10197-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10197-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10197-109">Requirements</span></span>  
 <span data-ttu-id="10197-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10197-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10197-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10197-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10197-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10197-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10197-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10197-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10197-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10197-114">See also</span></span>
