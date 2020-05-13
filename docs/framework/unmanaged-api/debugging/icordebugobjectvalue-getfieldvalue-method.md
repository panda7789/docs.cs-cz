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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207593"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="3fff6-102">ICorDebugObjectValue::GetFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="3fff6-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="3fff6-103">Získá hodnotu zadaného pole zadané třídy pro tuto hodnotu objektu.</span><span class="sxs-lookup"><span data-stu-id="3fff6-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fff6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fff6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fff6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fff6-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="3fff6-106">pro Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou chcete získat hodnotu pole.</span><span class="sxs-lookup"><span data-stu-id="3fff6-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="3fff6-107">pro `mdFieldDef`Token, který odkazuje na metadata popisující pole.</span><span class="sxs-lookup"><span data-stu-id="3fff6-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3fff6-108">mimo Ukazatel na objekt "ICorDebugValue", který představuje hodnotu zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="3fff6-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fff6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fff6-109">Remarks</span></span>  
 <span data-ttu-id="3fff6-110">Třída zadaná v `pClass` parametru musí být v hierarchii třídy Value objektu a pole musí být pole této třídy.</span><span class="sxs-lookup"><span data-stu-id="3fff6-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="3fff6-111">`GetFieldValue`Metoda bude stále úspěšná pro obecné objekty a obecné třídy.</span><span class="sxs-lookup"><span data-stu-id="3fff6-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="3fff6-112">Například pokud MyDictionary \< V> dědí z \< řetězce slovníku, V> a hodnota objektu je typu MyDictionary \< Int32>, předáním `ICorDebugClass` objektu pro slovník \< k, v> se úspěšně získá pole \< řetězce slovníku, Int32>.</span><span class="sxs-lookup"><span data-stu-id="3fff6-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fff6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fff6-113">Requirements</span></span>  
 <span data-ttu-id="3fff6-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fff6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fff6-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3fff6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fff6-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3fff6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fff6-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fff6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fff6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fff6-118">See also</span></span>
