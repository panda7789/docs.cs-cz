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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085139"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="da268-102">ICorDebugEval::CreateValue – metoda</span><span class="sxs-lookup"><span data-stu-id="da268-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="da268-103">Vytvoří hodnotu zadaného typu s počáteční hodnotou 0 nebo null.</span><span class="sxs-lookup"><span data-stu-id="da268-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="da268-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="da268-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="da268-105">Místo toho použijte [ICorDebugEval2:: createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="da268-105">Use [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da268-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da268-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da268-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="da268-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="da268-108">pro Hodnota výčtu [CorElementType –](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) , která určuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da268-108">[in] A value of the [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="da268-109">pro Ukazatel na objekt [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) , který určuje třídu hodnoty, pokud typ není primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="da268-109">[in] Pointer to an [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="da268-110">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="da268-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da268-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da268-111">Remarks</span></span>  
 <span data-ttu-id="da268-112">`CreateValue` vytvoří objekt `ICorDebugValue` daného typu pro výhradní účely jeho použití ve vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="da268-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="da268-113">Tento objekt hodnoty lze použít k předání konstant uživatele jako parametrů.</span><span class="sxs-lookup"><span data-stu-id="da268-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="da268-114">Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nula nebo null.</span><span class="sxs-lookup"><span data-stu-id="da268-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="da268-115">Pomocí [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) nastavte hodnotu primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="da268-115">Use [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="da268-116">Pokud je hodnota `elementType` ELEMENT_TYPE_CLASS, získáte "ICorDebugReferenceValue" (vrácený v `ppValue`) představující odkaz na objekt null.</span><span class="sxs-lookup"><span data-stu-id="da268-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="da268-117">Tento objekt lze použít k předání hodnoty null do vyhodnocení funkce, které má parametry objektu reference.</span><span class="sxs-lookup"><span data-stu-id="da268-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="da268-118">Nemůžete nastavit `ICorDebugValue` na cokoli. vždycky zůstane null.</span><span class="sxs-lookup"><span data-stu-id="da268-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da268-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da268-119">Requirements</span></span>  
 <span data-ttu-id="da268-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da268-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da268-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da268-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da268-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da268-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da268-123">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="da268-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da268-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da268-124">See also</span></span>

- [<span data-ttu-id="da268-125">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="da268-125">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="da268-126">Rozhraní ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="da268-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
