---
title: "ICLRDataTarget::Request – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e7bde3a0bc26a6bc93124fa835c4203cd596906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="d76bd-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="d76bd-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="d76bd-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup požádat o operaci podle definice implementace.</span><span class="sxs-lookup"><span data-stu-id="d76bd-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d76bd-104">Syntax</span></span>  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d76bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d76bd-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="d76bd-106">[v] Uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="d76bd-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="d76bd-107">[v] Velikost vstupní vyrovnávací paměť, která se používá k příchozího požadavku.</span><span class="sxs-lookup"><span data-stu-id="d76bd-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="d76bd-108">[v] Vyrovnávací paměť obsahující žádosti.</span><span class="sxs-lookup"><span data-stu-id="d76bd-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="d76bd-109">[v] Velikost výstupní vyrovnávací paměť, která se používá k odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d76bd-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="d76bd-110">[out] Vyrovnávací paměť s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="d76bd-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d76bd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d76bd-111">Remarks</span></span>  
 <span data-ttu-id="d76bd-112">`Request` Metoda usnadňuje přidání neurčené vlastní operace.</span><span class="sxs-lookup"><span data-stu-id="d76bd-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="d76bd-113">To znamená tato metoda zajišťuje rozšiřitelnost bez nutnosti revizi definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d76bd-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="d76bd-114">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d76bd-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d76bd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d76bd-115">Requirements</span></span>  
 <span data-ttu-id="d76bd-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d76bd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d76bd-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d76bd-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d76bd-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d76bd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d76bd-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d76bd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76bd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d76bd-120">See Also</span></span>  
 [<span data-ttu-id="d76bd-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d76bd-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
