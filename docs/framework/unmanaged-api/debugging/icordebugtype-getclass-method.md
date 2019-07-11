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
ms.openlocfilehash: bd68df77adafb8b21e7684b28fe978722ca37e16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736789"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="ae773-102">ICorDebugType::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="ae773-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="ae773-103">Získá ukazatel rozhraní k ICorDebugClass, který představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="ae773-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae773-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae773-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae773-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae773-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="ae773-106">[out] Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje obecný typ bez instancí.</span><span class="sxs-lookup"><span data-stu-id="ae773-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae773-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae773-107">Remarks</span></span>  
 <span data-ttu-id="ae773-108">`GetClass` může být volána pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="ae773-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="ae773-109">Volání [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) před voláním `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="ae773-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="ae773-110">Pokud `ICorDebugType::GetType` vrací hodnotu corelementtype –, který je za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` zjistit nevytvořeným instancím typu pro obecný typ může být volána.</span><span class="sxs-lookup"><span data-stu-id="ae773-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae773-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae773-111">Requirements</span></span>  
 <span data-ttu-id="ae773-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae773-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae773-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae773-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae773-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae773-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae773-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae773-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
