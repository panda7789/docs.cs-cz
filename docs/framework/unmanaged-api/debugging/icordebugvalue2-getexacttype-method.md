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
ms.openlocfilehash: f1f8292a6964a6b25e228fcd07ab21a7ee5f5a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423329"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="dae49-102">ICorDebugValue2::GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="dae49-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="dae49-103">Získá ukazatele rozhraní pro objekt "ICorDebugType", který představuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dae49-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dae49-104">Syntax</span></span>  
  
```  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dae49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dae49-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="dae49-106">[out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje <xref:System.Type> hodnoty představuje tento objekt "icordebugvalue2 –".</span><span class="sxs-lookup"><span data-stu-id="dae49-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dae49-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dae49-107">Remarks</span></span>  
 <span data-ttu-id="dae49-108">Obecné typy podporující `GetExactType` metoda nahrazuje i [icordebugobjectvalue::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) metody, každý z které návratový informace o typu hodnoty .</span><span class="sxs-lookup"><span data-stu-id="dae49-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae49-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dae49-109">Requirements</span></span>  
 <span data-ttu-id="dae49-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae49-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dae49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dae49-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dae49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dae49-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae49-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dae49-114">See Also</span></span>  
 
