---
title: ICLRDataTarget::Request – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bd3bc239d0101f02cd515b0ec2a8bec3372882
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596901"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="6c5be-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="6c5be-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="6c5be-103">Voláno rozhraním common language runtime (CLR) data access services požádat o operaci, jak je definováno implementací.</span><span class="sxs-lookup"><span data-stu-id="6c5be-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c5be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c5be-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6c5be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c5be-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="6c5be-106">[in] Uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="6c5be-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="6c5be-107">[in] Velikost vstupní vyrovnávací paměti, který se používá pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="6c5be-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="6c5be-108">[in] Vyrovnávací paměť obsahující žádost.</span><span class="sxs-lookup"><span data-stu-id="6c5be-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="6c5be-109">[in] Velikost výstupní vyrovnávací paměť, která se používá pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="6c5be-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="6c5be-110">[out] Vyrovnávací paměť s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="6c5be-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c5be-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c5be-111">Remarks</span></span>  
 <span data-ttu-id="6c5be-112">`Request` Metoda usnadňuje přidávání neurčené vlastní operace.</span><span class="sxs-lookup"><span data-stu-id="6c5be-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="6c5be-113">To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti revize definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6c5be-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="6c5be-114">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c5be-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c5be-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c5be-115">Requirements</span></span>  
 <span data-ttu-id="6c5be-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c5be-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c5be-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6c5be-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6c5be-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c5be-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c5be-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c5be-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5be-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c5be-120">See also</span></span>
- [<span data-ttu-id="6c5be-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c5be-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
