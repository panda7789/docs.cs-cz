---
title: ICorDebugObjectValue::GetFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d4e4a2dd9d1f419c94152e4131997f39b2d3b83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493866"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="ea69d-102">ICorDebugObjectValue::GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="ea69d-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="ea69d-103">Získá hodnotu zadaného pole ze zadané třídy pro tuto hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="ea69d-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea69d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea69d-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea69d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea69d-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="ea69d-106">[in] Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou má být získána hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="ea69d-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="ea69d-107">[in] `mdFieldDef` Token, který odkazuje na metadata popisující pole.</span><span class="sxs-lookup"><span data-stu-id="ea69d-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ea69d-108">[out] Ukazatel na objekt "ICorDebugValue", která představuje hodnotu zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="ea69d-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea69d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea69d-109">Remarks</span></span>  
 <span data-ttu-id="ea69d-110">Třída zadaná v `pClass` parametr, musí být v hierarchii třídy hodnota objektu a pole této třídy musí být pole.</span><span class="sxs-lookup"><span data-stu-id="ea69d-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="ea69d-111">`GetFieldValue` Metoda i tak proběhne úspěšně obecných objektů a obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="ea69d-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="ea69d-112">Například pokud MyDictionary\<V > dědí ze slovníku\<string, V >, a hodnota objekt je typu MyDictionary\<int32 >, předejte `ICorDebugClass` objekt slovníku\<K, V > bude úspěšně získat pole slovníku\<řetězec, int32 >.</span><span class="sxs-lookup"><span data-stu-id="ea69d-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea69d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea69d-113">Requirements</span></span>  
 <span data-ttu-id="ea69d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea69d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea69d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea69d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea69d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea69d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea69d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea69d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea69d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea69d-118">See also</span></span>


