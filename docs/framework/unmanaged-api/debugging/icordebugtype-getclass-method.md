---
title: ICorDebugType::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499534"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="54463-102">ICorDebugType::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="54463-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="54463-103">Získá ukazatel rozhraní k ICorDebugClass, který představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="54463-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54463-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54463-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54463-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54463-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="54463-106">[out] Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="54463-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54463-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54463-107">Remarks</span></span>  
 <span data-ttu-id="54463-108">`GetClass` může být volána pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="54463-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="54463-109">Volání [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) před voláním `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="54463-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="54463-110">Pokud `ICorDebugType::GetType` vrací hodnotu corelementtype –, který je za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` zjistit nevytvořeným instancím typu pro obecný typ může být volána.</span><span class="sxs-lookup"><span data-stu-id="54463-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54463-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54463-111">Requirements</span></span>  
 <span data-ttu-id="54463-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54463-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54463-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54463-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54463-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54463-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54463-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54463-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
