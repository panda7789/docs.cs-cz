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
ms.openlocfilehash: e9005dd8fde0d7258bd1dd48b561e4925e87733b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698067"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="b0526-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="b0526-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="b0526-103">Voláno rozhraním common language runtime (CLR) data access services požádat o operaci, jak je definováno implementací.</span><span class="sxs-lookup"><span data-stu-id="b0526-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0526-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0526-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b0526-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0526-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="b0526-106">[in] Uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="b0526-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="b0526-107">[in] Velikost vstupní vyrovnávací paměti, který se používá pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="b0526-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="b0526-108">[in] Vyrovnávací paměť obsahující žádost.</span><span class="sxs-lookup"><span data-stu-id="b0526-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="b0526-109">[in] Velikost výstupní vyrovnávací paměť, která se používá pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="b0526-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="b0526-110">[out] Vyrovnávací paměť s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="b0526-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0526-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0526-111">Remarks</span></span>  
 <span data-ttu-id="b0526-112">`Request` Metoda usnadňuje přidávání neurčené vlastní operace.</span><span class="sxs-lookup"><span data-stu-id="b0526-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="b0526-113">To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti revize definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0526-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="b0526-114">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0526-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0526-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0526-115">Requirements</span></span>  
 <span data-ttu-id="b0526-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0526-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0526-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b0526-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b0526-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0526-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0526-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0526-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0526-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0526-120">See also</span></span>

- [<span data-ttu-id="b0526-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0526-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
