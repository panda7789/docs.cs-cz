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
ms.openlocfilehash: 230666cefdadd56465fac35222500ad4b6da67e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418298"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="5dfa6-102">ICorDebugObjectValue::GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="5dfa6-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="5dfa6-103">Získá hodnotu zadaného pole pro zadanou třídu pro tuto hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dfa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dfa6-104">Syntax</span></span>  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dfa6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dfa6-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="5dfa6-106">[v] Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou má být získána hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="5dfa6-107">[v] `mdFieldDef` Token, který odkazuje na metadata popisující pole.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5dfa6-108">[out] Ukazatel na objekt "ICorDebugValue", který představuje hodnotu zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dfa6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5dfa6-109">Remarks</span></span>  
 <span data-ttu-id="5dfa6-110">Zadaná třída, v `pClass` parametr, musí být v hierarchii třídy hodnota objektu, a v poli musí být pole této třídy.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="5dfa6-111">`GetFieldValue` Metoda bude stále úspěšné pro obecné objekty a obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="5dfa6-112">Například pokud MyDictionary\<V > dědí ze slovníku\<řetězce, V >, a hodnota objekt je typu MyDictionary\<int32 >, předejte `ICorDebugClass` objekt pro slovník\<tisíc, V > bude byl úspěšně načten pole slovník\<string, int32 >.</span><span class="sxs-lookup"><span data-stu-id="5dfa6-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dfa6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5dfa6-113">Requirements</span></span>  
 <span data-ttu-id="5dfa6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dfa6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dfa6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dfa6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dfa6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dfa6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dfa6-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dfa6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfa6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dfa6-118">See Also</span></span>  
    
 
