---
title: "ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ece07fcffbc0d0e6b8cf06cc04866c1b651e6a01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="d23ca-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="d23ca-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="d23ca-103">Získá hodnotu argumentu nebo místní proměnné, která je uložená v dvě zaregistruje zadaný pro tento nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="d23ca-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d23ca-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d23ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d23ca-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="d23ca-106">[v] Hodnota výčtu "CorDebugRegister", který určuje registrace obsahující slovo vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d23ca-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="d23ca-107">[v] Hodnota `CorDebugRegister` výčet, který určuje registru obsahujícího nízkou slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d23ca-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d23ca-108">[v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="d23ca-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d23ca-109">[v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="d23ca-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d23ca-110">[out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty uložené v zadané Registry.</span><span class="sxs-lookup"><span data-stu-id="d23ca-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d23ca-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d23ca-111">Remarks</span></span>  
 <span data-ttu-id="d23ca-112">`GetLocalDoubleRegisterValue` Metodu lze použít buď v nativní rámce nebo v běhu (JIT)-zkompilovat rámce.</span><span class="sxs-lookup"><span data-stu-id="d23ca-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d23ca-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d23ca-113">Requirements</span></span>  
 <span data-ttu-id="d23ca-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d23ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d23ca-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d23ca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d23ca-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d23ca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d23ca-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d23ca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23ca-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d23ca-118">See Also</span></span>  
 
