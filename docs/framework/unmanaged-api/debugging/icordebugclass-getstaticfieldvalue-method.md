---
title: ICorDebugClass::GetStaticFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7649d91ca2b654952d1d5ab0d45f7903d3c46a32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745538"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="ea2c0-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="ea2c0-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="ea2c0-103">Získá hodnotu zadané statické pole.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea2c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea2c0-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="ea2c0-106">[in] Pole `Def` token, který odkazuje na pole, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="ea2c0-107">[in] Ukazatel na objekt ICorDebugFrame představující rámec, který se má použít k rozlišení mezi vlákno, místní nebo statistika domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="ea2c0-108">Pokud je statická pole relativní vzhledem k vlákno, kontext nebo doménu aplikace, rámce určí správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ea2c0-109">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu statické pole.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2c0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea2c0-110">Remarks</span></span>  
 <span data-ttu-id="ea2c0-111">Pro parametrizované typy statické pole hodnotu vzhledem ke konkrétní vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="ea2c0-112">Proto pokud konstruktor třídy má parametry typu <xref:System.Type>, volání [icordebugtype::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) místo `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="ea2c0-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2c0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea2c0-113">Requirements</span></span>  
 <span data-ttu-id="ea2c0-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2c0-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea2c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea2c0-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea2c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2c0-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
