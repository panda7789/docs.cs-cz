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
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379940"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="c3a20-102">ICorDebugType::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c3a20-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="c3a20-103">Získá ukazatel rozhraní na objekt ICorDebugValue, který obsahuje hodnotu statického pole, na které se odkazuje pomocí zadaného tokenu pole v zadaném bloku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c3a20-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3a20-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="c3a20-106">pro `mdFieldDef`Token, který určuje statické pole.</span><span class="sxs-lookup"><span data-stu-id="c3a20-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="c3a20-107">pro Ukazatel na ICorDebugFrame, který představuje rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c3a20-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c3a20-108">mimo Ukazatel na adresu `ICorDebugValue` , která obsahuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="c3a20-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a20-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3a20-109">Remarks</span></span>  
 <span data-ttu-id="c3a20-110">`GetStaticFieldValue`Metoda může být použita pouze v případě, že je typ ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, jak je uvedeno v metodě [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3a20-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="c3a20-111">U neobecných typů operace prováděná `GetStaticFieldValue` je shodná s voláním [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) na objektu ICorDebugClass, který vrací [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3a20-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="c3a20-112">U obecných typů bude hodnota statického pole relativní vzhledem k konkrétní instanci.</span><span class="sxs-lookup"><span data-stu-id="c3a20-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="c3a20-113">Také, pokud by mohlo být statické pole relativní vzhledem ke vláknu, kontextu nebo doméně aplikace, pak rámec zásobníku pomůže ladicímu programu určit správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c3a20-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a20-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3a20-114">Remarks</span></span>  
 <span data-ttu-id="c3a20-115">`GetStaticFieldValue`lze ji použít pouze v případě, že volání `ICorDebugType::GetType` vrátí hodnotu ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="c3a20-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a20-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3a20-116">Requirements</span></span>  
 <span data-ttu-id="c3a20-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a20-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a20-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3a20-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3a20-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c3a20-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a20-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a20-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
