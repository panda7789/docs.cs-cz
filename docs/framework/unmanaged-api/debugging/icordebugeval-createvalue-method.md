---
title: ICorDebugEval::CreateValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d67784daee055106f104d74d098b9926c6de2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417109"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="3b94d-102">ICorDebugEval::CreateValue – metoda</span><span class="sxs-lookup"><span data-stu-id="3b94d-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="3b94d-103">Vytvoří hodnotu zadaného typu, s počáteční hodnotou nula nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3b94d-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="3b94d-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="3b94d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3b94d-105">Použití [icordebugeval2::createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="3b94d-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b94d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b94d-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b94d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b94d-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="3b94d-108">[v] Hodnota [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) výčet, který určuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3b94d-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="3b94d-109">[v] Ukazatel na [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objekt, který určuje třída hodnoty, pokud typ není primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="3b94d-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3b94d-110">[out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3b94d-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b94d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b94d-111">Remarks</span></span>  
 <span data-ttu-id="3b94d-112">`CreateValue` vytvoří `ICorDebugValue` objekt daného typu za účelem používání ve vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="3b94d-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="3b94d-113">Tento objekt hodnota slouží k předávání konstanty uživatele jako parametry.</span><span class="sxs-lookup"><span data-stu-id="3b94d-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="3b94d-114">Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nulová nebo má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3b94d-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="3b94d-115">Použití [icordebuggenericvalue::SetValue –](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) nastavit hodnotu primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="3b94d-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="3b94d-116">Pokud hodnota `elementType` je ELEMENT_TYPE_CLASS, získat "ICorDebugReferenceValue" (vrátí `ppValue`) představující odkaz na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3b94d-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="3b94d-117">Tento objekt můžete použít k vyhodnocení funkce, s parametry odkaz na objekt předat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3b94d-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="3b94d-118">Nelze nastavit `ICorDebugValue` k ničemu; vždy zůstává hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3b94d-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b94d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b94d-119">Requirements</span></span>  
 <span data-ttu-id="3b94d-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b94d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b94d-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b94d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b94d-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b94d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b94d-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3b94d-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b94d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b94d-124">See Also</span></span>  
    
 [<span data-ttu-id="3b94d-125">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="3b94d-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 <span data-ttu-id="3b94d-126">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="3b94d-126">ICorDebugValue</span></span>
