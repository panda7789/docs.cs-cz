---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abaa543299dec74d769b91ca3b21d76863624f13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484937"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="a1211-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a1211-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="a1211-103">Získá hodnotu argumentu nebo místní proměnná, z nichž nízké word a vysokou word jsou uloženy v zadaný registr a umístění v paměti, v uvedeném pořadí, tato nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="a1211-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1211-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1211-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1211-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1211-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="a1211-106">[in] A `CORDB_ADDRESS` hodnota, která určuje umístění v paměti obsahují slovo vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a1211-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="a1211-107">[in] Hodnota výčtu "cordebugregister –", který určuje do registru, které obsahují slovo nízké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a1211-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a1211-108">[in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="a1211-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="a1211-109">[in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a1211-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a1211-110">[out] Ukazatel na adresu "ICorDebugValue" objekt představující získanou hodnotu, která je uložena v zadaném umístění registru a paměti.</span><span class="sxs-lookup"><span data-stu-id="a1211-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1211-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1211-111">Requirements</span></span>  
 <span data-ttu-id="a1211-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1211-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1211-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1211-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1211-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1211-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1211-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1211-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1211-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1211-116">See also</span></span>

