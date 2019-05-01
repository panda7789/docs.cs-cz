---
title: ICorDebugNativeFrame::GetLocalRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f53c8290271391e52176f8364b592ce6b46faf71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994627"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="8b962-102">ICorDebugNativeFrame::GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="8b962-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="8b962-103">Získá hodnotu argumentu nebo místní proměnná, která je uložena do zadaného registru pro tuto nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="8b962-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b962-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b962-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b962-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b962-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="8b962-106">[in] Hodnota výčtu "cordebugregister –", který určuje do registru, který obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8b962-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8b962-107">[in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="8b962-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8b962-108">[in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8b962-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8b962-109">[out] Ukazatel na adresu "ICorDebugValue" objekt představující získanou hodnotu, která je uložena do zadaného registru.</span><span class="sxs-lookup"><span data-stu-id="8b962-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b962-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b962-110">Remarks</span></span>  
 <span data-ttu-id="8b962-111">`GetLocalRegisterValue` Metodu je možné použít ve službě je nativní rámec nebo just-in-time (JIT)-zkompilován rámce.</span><span class="sxs-lookup"><span data-stu-id="8b962-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b962-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b962-112">Requirements</span></span>  
 <span data-ttu-id="8b962-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b962-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b962-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b962-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b962-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b962-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b962-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b962-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b962-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b962-117">See also</span></span>
