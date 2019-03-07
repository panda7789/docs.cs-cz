---
title: ICorDebugType::GetStaticFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485392"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="90266-102">ICorDebugType::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="90266-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="90266-103">Získá ukazatel rozhraní na ICorDebugValue objekt, který obsahuje hodnotu statické pole určené pole odkazuje tokenu v určeném zásobníku rámce.</span><span class="sxs-lookup"><span data-stu-id="90266-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90266-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90266-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90266-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90266-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="90266-106">[in] `mdFieldDef` Token, který určuje statické pole.</span><span class="sxs-lookup"><span data-stu-id="90266-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="90266-107">[in] Ukazatel na ICorDebugFrame, který představuje rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90266-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="90266-108">[out] Ukazatel na adresu `ICorDebugValue` , který obsahuje hodnotu statické pole.</span><span class="sxs-lookup"><span data-stu-id="90266-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90266-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90266-109">Remarks</span></span>  
 <span data-ttu-id="90266-110">`GetStaticFieldValue` – Metoda může použít pouze v případě, že typ je za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, znázorněné [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="90266-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="90266-111">Pro obecné typy, operace provedena `GetStaticFieldValue` je stejný jako volání [icordebugclass::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass objektu, který je vrácený [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="90266-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="90266-112">Pro obecné typy bude hodnota statické pole vzhledem ke konkrétní vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="90266-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="90266-113">Navíc pokud statické pole může být může být relativní vzhledem k vlákno, kontext nebo doménu aplikace, pak rámce zásobníku pomůže ladicí program určit správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90266-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90266-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90266-114">Remarks</span></span>  
 <span data-ttu-id="90266-115">`GetStaticFieldValue` se dá použít jenom při volání `ICorDebugType::GetType` vrací hodnotu za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="90266-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90266-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90266-116">Requirements</span></span>  
 <span data-ttu-id="90266-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90266-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90266-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90266-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90266-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90266-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90266-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90266-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
