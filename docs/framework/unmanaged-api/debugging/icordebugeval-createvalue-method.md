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
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976249"
---
# <a name="icordebugevalcreatevalue-method"></a><span data-ttu-id="82360-102">ICorDebugEval::CreateValue – metoda</span><span class="sxs-lookup"><span data-stu-id="82360-102">ICorDebugEval::CreateValue Method</span></span>
<span data-ttu-id="82360-103">Vytvoří hodnotu zadaného typu s počáteční hodnotou 0 nebo null.</span><span class="sxs-lookup"><span data-stu-id="82360-103">Creates a value of the specified type, with an initial value of zero or null.</span></span>  
  
 <span data-ttu-id="82360-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="82360-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="82360-105">Místo toho použijte [ICorDebugEval2:: createvaluefortype –](icordebugeval2-createvaluefortype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="82360-105">Use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82360-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82360-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82360-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="82360-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="82360-108">pro Hodnota výčtu [CorElementType –](../metadata/corelementtype-enumeration.md) , která určuje typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="82360-108">[in] A value of the [CorElementType](../metadata/corelementtype-enumeration.md) enumeration that specifies the type of the value.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="82360-109">pro Ukazatel na objekt [ICorDebugClass](icordebugclass-interface.md) , který určuje třídu hodnoty, pokud typ není primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="82360-109">[in] Pointer to an [ICorDebugClass](icordebugclass-interface.md) object that specifies the class of the value, if the type is not a primitive type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="82360-110">mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82360-110">[out] Pointer to the address of an "ICorDebugValue" object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82360-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82360-111">Remarks</span></span>  
 <span data-ttu-id="82360-112">`CreateValue`vytvoří `ICorDebugValue` objekt daného typu pro výhradní účely jeho použití ve vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="82360-112">`CreateValue` creates an `ICorDebugValue` object of the given type for the sole purpose of using it in a function evaluation.</span></span> <span data-ttu-id="82360-113">Tento objekt hodnoty lze použít k předání konstant uživatele jako parametrů.</span><span class="sxs-lookup"><span data-stu-id="82360-113">This value object can be used to pass user constants as parameters.</span></span>  
  
 <span data-ttu-id="82360-114">Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nula nebo null.</span><span class="sxs-lookup"><span data-stu-id="82360-114">If the type of the value is a primitive type, its initial value is zero or null.</span></span> <span data-ttu-id="82360-115">Pomocí [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) nastavte hodnotu primitivního typu.</span><span class="sxs-lookup"><span data-stu-id="82360-115">Use [ICorDebugGenericValue::SetValue](icordebuggenericvalue-setvalue-method.md) to set the value of a primitive type.</span></span>  
  
 <span data-ttu-id="82360-116">Pokud `elementType` je hodnota ELEMENT_TYPE_CLASS, získáte "ICorDebugReferenceValue" (vrácený v `ppValue`) reprezentující odkaz na objekt null.</span><span class="sxs-lookup"><span data-stu-id="82360-116">If the value of `elementType` is ELEMENT_TYPE_CLASS, you get an "ICorDebugReferenceValue" (returned in `ppValue`) representing the null object reference.</span></span> <span data-ttu-id="82360-117">Tento objekt lze použít k předání hodnoty null do vyhodnocení funkce, které má parametry objektu reference.</span><span class="sxs-lookup"><span data-stu-id="82360-117">You can use this object to pass null to a function evaluation that has object reference parameters.</span></span> <span data-ttu-id="82360-118">Nemůžete nastavit `ICorDebugValue` na cokoli; vždycky zůstane null.</span><span class="sxs-lookup"><span data-stu-id="82360-118">You cannot set the `ICorDebugValue` to anything; it always remains null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82360-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82360-119">Requirements</span></span>  
 <span data-ttu-id="82360-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82360-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82360-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82360-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82360-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82360-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82360-123">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="82360-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82360-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="82360-124">See also</span></span>

- [<span data-ttu-id="82360-125">CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="82360-125">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)
- [<span data-ttu-id="82360-126">ICorDebugEval – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82360-126">ICorDebugEval Interface</span></span>](icordebugeval-interface.md)
