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
ms.openlocfilehash: 0af820b590271e16cbfb443c193fd0afb4ed3358
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604109"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="ef059-102">ICorDebugEval::CreateValue – metoda</span><span class="sxs-lookup"><span data-stu-id="ef059-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="ef059-103">Vytvoří hodnotu zadaného typu, s počáteční hodnotou nula nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ef059-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="ef059-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef059-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ef059-105">Použití [icordebugeval2::createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="ef059-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef059-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef059-106">Syntax</span></span>  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef059-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef059-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="ef059-108">[in] Hodnota [corelementtype –](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) výčet, který určuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ef059-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="ef059-109">[in] Ukazatel [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objekt, který určuje třída hodnotu, pokud typ není primitivním typem.</span><span class="sxs-lookup"><span data-stu-id="ef059-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ef059-110">[out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ef059-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef059-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef059-111">Remarks</span></span>  
 <span data-ttu-id="ef059-112">`CreateValue` vytvoří `ICorDebugValue` objekt daného typu pouze za účelem použití v vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="ef059-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="ef059-113">Tento objekt hodnotu lze předat jako parametry konstanty uživatele.</span><span class="sxs-lookup"><span data-stu-id="ef059-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="ef059-114">Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nula nebo mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ef059-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="ef059-115">Použití [icordebuggenericvalue::SetValue –](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) k nastavení hodnoty primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="ef059-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="ef059-116">Pokud hodnota `elementType` je za řetězcem ELEMENT_TYPE_CLASS, získáte "ICorDebugReferenceValue" (vrácené v `ppValue`) představující odkaz na objekt s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ef059-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="ef059-117">Tento objekt slouží k vyhodnocení funkce, která má parametry objektů reference předat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ef059-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="ef059-118">Nelze nastavit `ICorDebugValue` k ničemu; vždy zůstane hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ef059-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef059-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef059-119">Requirements</span></span>  
 <span data-ttu-id="ef059-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef059-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef059-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef059-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef059-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef059-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef059-123">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="ef059-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef059-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef059-124">See also</span></span>

- <span data-ttu-id="ef059-125">[CreateValueForType Method](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="ef059-125">[CreateValueForType Method](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) ICorDebugValue</span></span>
