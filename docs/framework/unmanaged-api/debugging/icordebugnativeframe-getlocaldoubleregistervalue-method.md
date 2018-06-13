---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9de77f942a1b89b0ab11ef71229e491a5305cafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420749"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="695e1-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="695e1-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="695e1-103">Získá hodnotu argumentu nebo místní proměnné, která je uložená v dvě zaregistruje zadaný pro tento nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="695e1-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="695e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="695e1-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="695e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="695e1-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="695e1-106">[v] Hodnota výčtu "CorDebugRegister", který určuje registrace obsahující slovo vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="695e1-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="695e1-107">[v] Hodnota `CorDebugRegister` výčet, který určuje registru obsahujícího nízkou slovo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="695e1-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="695e1-108">[v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="695e1-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="695e1-109">[v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="695e1-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="695e1-110">[out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty uložené v zadané Registry.</span><span class="sxs-lookup"><span data-stu-id="695e1-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="695e1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="695e1-111">Remarks</span></span>  
 <span data-ttu-id="695e1-112">`GetLocalDoubleRegisterValue` Metodu lze použít buď v nativní rámce nebo v běhu (JIT)-zkompilovat rámce.</span><span class="sxs-lookup"><span data-stu-id="695e1-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="695e1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="695e1-113">Requirements</span></span>  
 <span data-ttu-id="695e1-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="695e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="695e1-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="695e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="695e1-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="695e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="695e1-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="695e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695e1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="695e1-118">See Also</span></span>  
 
