---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26cd30be591c4167fa6a6e4d19ba9d1c909c6428
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145766"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="c42fe-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c42fe-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="c42fe-103">Získá hodnotu argumentu nebo místní proměnné, které s nízkou word a vysokou word jsou uloženy v umístění v paměti a zadaný registr, v uvedeném pořadí, tato nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="c42fe-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c42fe-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c42fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c42fe-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="c42fe-106">[in] Hodnota, která určuje do registru, které obsahují slovo vysoké hodnoty výčtu "cordebugregister –".</span><span class="sxs-lookup"><span data-stu-id="c42fe-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="c42fe-107">[in] A `CORDB_ADDRESS` hodnota, která určuje umístění v paměti obsahují slovo nízké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c42fe-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c42fe-108">[in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="c42fe-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c42fe-109">[in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c42fe-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c42fe-110">[out] Ukazatel na adresu "ICorDebugValue" objekt představující získanou hodnotu, která je uložena v zadaném umístění registru a paměti.</span><span class="sxs-lookup"><span data-stu-id="c42fe-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42fe-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c42fe-111">Requirements</span></span>  
 <span data-ttu-id="c42fe-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c42fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42fe-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c42fe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c42fe-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c42fe-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c42fe-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c42fe-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c42fe-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c42fe-116">See also</span></span>
