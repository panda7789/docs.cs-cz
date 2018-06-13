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
ms.openlocfilehash: 5419d2e6932e08d05c8336d473cf68bd16058a48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417268"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="93763-102">ICorDebugNativeFrame::GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="93763-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="93763-103">Získá hodnotu argumentu nebo místní proměnné, která je uložena v umístění zadaná paměťová tato nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="93763-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93763-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93763-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93763-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93763-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="93763-106">[v] A `CORDB_ADDRESS` hodnotu, která určuje umístění v paměti, který obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="93763-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="93763-107">[v] Celé číslo, které určuje velikost podpis binární metadat, který se odkazuje `pvSigBlob` parametr.</span><span class="sxs-lookup"><span data-stu-id="93763-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="93763-108">[v] A `PCCOR_SIGNATURE` hodnotu, která ukazuje na binární metadata podpis hodnotu typu.</span><span class="sxs-lookup"><span data-stu-id="93763-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="93763-109">[out] Ukazatel na adresu "ICorDebugValue" objekt, který reprezentuje načtené hodnoty, který je uložen v umístění zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="93763-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93763-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93763-110">Requirements</span></span>  
 <span data-ttu-id="93763-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93763-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93763-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93763-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93763-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93763-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93763-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93763-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93763-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="93763-115">See Also</span></span>  
 
