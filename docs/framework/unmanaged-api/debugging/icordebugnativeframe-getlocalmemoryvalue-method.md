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
ms.openlocfilehash: cee095003c136142052b8f946fa8227927c80ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096869"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="101b3-102">ICorDebugNativeFrame::GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="101b3-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="101b3-103">Získá hodnotu argumentu nebo místní proměnné, která je uložena v zadaném umístění v paměti pro tento nativní rámec.</span><span class="sxs-lookup"><span data-stu-id="101b3-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="101b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="101b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="101b3-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="101b3-106">pro Hodnota `CORDB_ADDRESS`, která určuje umístění paměti obsahující hodnotu.</span><span class="sxs-lookup"><span data-stu-id="101b3-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="101b3-107">pro Celé číslo, které určuje velikost binárního podpisu metadat, na které odkazuje parametr `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="101b3-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="101b3-108">pro Hodnota `PCCOR_SIGNATURE`, která odkazuje na binární signaturu metadat typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="101b3-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="101b3-109">mimo Ukazatel na adresu objektu "ICorDebugValue" představující načtenou hodnotu, která je uložena v zadaném umístění v paměti.</span><span class="sxs-lookup"><span data-stu-id="101b3-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="101b3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="101b3-110">Requirements</span></span>  
 <span data-ttu-id="101b3-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101b3-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="101b3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="101b3-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="101b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="101b3-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101b3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="101b3-115">See also</span></span>
