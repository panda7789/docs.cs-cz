---
title: ICorDebugNativeFrame::GetLocalMemoryValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c44f3e369ac64773811a6aea74756783dedd2fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209460"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="3186e-102">ICorDebugNativeFrame::GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="3186e-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="3186e-103">Získá hodnotu argumentu nebo místní proměnná, která je uložena v zadaném umístění v paměti pro tuto nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="3186e-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3186e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3186e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3186e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3186e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3186e-106">[in] A `CORDB_ADDRESS` hodnota, která určuje umístění v paměti, který obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3186e-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3186e-107">[in] Celé číslo, které určuje velikost podpisu binární metadat, který se odkazuje `pvSigBlob` parametru.</span><span class="sxs-lookup"><span data-stu-id="3186e-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3186e-108">[in] A `PCCOR_SIGNATURE` hodnotu, která odkazuje na podpis metadat binární typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3186e-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3186e-109">[out] Ukazatel na adresu "ICorDebugValue" objekt představující získanou hodnotu, která je uložena v zadaném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="3186e-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3186e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3186e-110">Requirements</span></span>  
 <span data-ttu-id="3186e-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3186e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3186e-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3186e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3186e-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3186e-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3186e-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3186e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3186e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3186e-115">See also</span></span>
