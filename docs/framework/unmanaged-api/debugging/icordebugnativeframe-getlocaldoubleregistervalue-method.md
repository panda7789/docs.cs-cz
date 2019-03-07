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
ms.openlocfilehash: 573949f50135ddf29ac9aa88bf4d1dd480001219
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471703"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="0f37e-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="0f37e-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="0f37e-103">Získá hodnotu argumentu nebo místní proměnná, která je uložena v dvě zadané registrů pro tuto nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="0f37e-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f37e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f37e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f37e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f37e-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="0f37e-106">[in] Hodnota, která určuje do registru, které obsahují slovo vysoké hodnoty výčtu "cordebugregister –".</span><span class="sxs-lookup"><span data-stu-id="0f37e-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="0f37e-107">[in] Hodnota `CorDebugRegister` výčet, který určuje do registru, které obsahují slovo nízké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0f37e-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0f37e-108">[in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="0f37e-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0f37e-109">[in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0f37e-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0f37e-110">[out] Ukazatel na adresu "ICorDebugValue" objekt představující načtené hodnoty uložené v zadané registrů.</span><span class="sxs-lookup"><span data-stu-id="0f37e-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f37e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f37e-111">Remarks</span></span>  
 <span data-ttu-id="0f37e-112">`GetLocalDoubleRegisterValue` Metodu je možné použít ve službě je nativní rámec nebo just-in-time (JIT)-zkompilován rámce.</span><span class="sxs-lookup"><span data-stu-id="0f37e-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f37e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f37e-113">Requirements</span></span>  
 <span data-ttu-id="0f37e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f37e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f37e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f37e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f37e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f37e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f37e-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f37e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f37e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f37e-118">See also</span></span>

