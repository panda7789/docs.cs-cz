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
ms.openlocfilehash: 4d3c3c0c5634653d14577de9a1334048d75216b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405623"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="25dd4-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="25dd4-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="25dd4-103">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="25dd4-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25dd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25dd4-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25dd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25dd4-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="25dd4-106">[v] Pole `Def` token, který odkazuje na pole, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="25dd4-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="25dd4-107">[v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, který se má použít k rozlišení mezi přístup z více vláken, kontext nebo statistika domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="25dd4-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="25dd4-108">Pokud statické pole je relativní vzhledem ke vlákno, kontextu nebo doménu aplikace, určí rámečku správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25dd4-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="25dd4-109">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="25dd4-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25dd4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25dd4-110">Remarks</span></span>  
 <span data-ttu-id="25dd4-111">Pro parametrizované typy hodnotu statických polí je relativní vzhledem ke konkrétní instance.</span><span class="sxs-lookup"><span data-stu-id="25dd4-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="25dd4-112">Proto pokud konstruktoru třídy mají parametry typu <xref:System.Type>, volání [icordebugtype::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) místo `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="25dd4-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25dd4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25dd4-113">Requirements</span></span>  
 <span data-ttu-id="25dd4-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25dd4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25dd4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25dd4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25dd4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25dd4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25dd4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25dd4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
