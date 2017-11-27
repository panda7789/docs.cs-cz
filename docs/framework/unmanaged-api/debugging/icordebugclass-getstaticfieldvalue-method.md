---
title: "ICorDebugClass::GetStaticFieldValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 15491728e225799eb0e934c9cc42a3967c19202e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="7a99f-102">ICorDebugClass::GetStaticFieldValue – metoda</span><span class="sxs-lookup"><span data-stu-id="7a99f-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="7a99f-103">Získá hodnotu zadaného pole statické.</span><span class="sxs-lookup"><span data-stu-id="7a99f-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a99f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a99f-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a99f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a99f-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="7a99f-106">[v] Pole `Def` token, který odkazuje na pole, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7a99f-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="7a99f-107">[v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, který se má použít k rozlišení mezi přístup z více vláken, kontext nebo statistika domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a99f-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="7a99f-108">Pokud statické pole je relativní vzhledem ke vlákno, kontextu nebo doménu aplikace, určí rámečku správnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7a99f-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7a99f-109">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu statického pole.</span><span class="sxs-lookup"><span data-stu-id="7a99f-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a99f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a99f-110">Remarks</span></span>  
 <span data-ttu-id="7a99f-111">Pro parametrizované typy hodnotu statických polí je relativní vzhledem ke konkrétní instance.</span><span class="sxs-lookup"><span data-stu-id="7a99f-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="7a99f-112">Proto pokud konstruktoru třídy mají parametry typu <xref:System.Type>, volání [icordebugtype::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) místo `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="7a99f-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a99f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a99f-113">Requirements</span></span>  
 <span data-ttu-id="7a99f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a99f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a99f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a99f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a99f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a99f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a99f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a99f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
