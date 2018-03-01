---
title: "ICorDebugClass::GetStaticFieldValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21176eb73b3655fe8bd4b2187b6da49a3c31bd82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="b670a-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b670a-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="b670a-103">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="b670a-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b670a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b670a-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b670a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b670a-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="b670a-106">[v] Pole `Def` token, který odkazuje na pole, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="b670a-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="b670a-107">[v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, který se má použít k rozlišení mezi přístup z více vláken, kontext nebo statistika domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b670a-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="b670a-108">Pokud statické pole je relativní vzhledem ke vlákno, kontextu nebo doménu aplikace, určí rámečku správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b670a-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b670a-109">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="b670a-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b670a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b670a-110">Remarks</span></span>  
 <span data-ttu-id="b670a-111">Pro parametrizované typy hodnotu statických polí je relativní vzhledem ke konkrétní instance.</span><span class="sxs-lookup"><span data-stu-id="b670a-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="b670a-112">Proto pokud konstruktoru třídy mají parametry typu <xref:System.Type>, volání [icordebugtype::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) místo `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="b670a-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b670a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b670a-113">Requirements</span></span>  
 <span data-ttu-id="b670a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b670a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b670a-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b670a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b670a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b670a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b670a-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b670a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
