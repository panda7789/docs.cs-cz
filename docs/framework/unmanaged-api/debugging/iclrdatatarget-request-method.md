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
ms.openlocfilehash: dc79277c75118b11766e66137284bd5655eed091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405369"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="04a43-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="04a43-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="04a43-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup požádat o operaci podle definice implementace.</span><span class="sxs-lookup"><span data-stu-id="04a43-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a43-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="04a43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04a43-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="04a43-106">[v] Uživatelem definované.</span><span class="sxs-lookup"><span data-stu-id="04a43-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="04a43-107">[v] Velikost vstupní vyrovnávací paměť, která se používá k příchozího požadavku.</span><span class="sxs-lookup"><span data-stu-id="04a43-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="04a43-108">[v] Vyrovnávací paměť obsahující žádosti.</span><span class="sxs-lookup"><span data-stu-id="04a43-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="04a43-109">[v] Velikost výstupní vyrovnávací paměť, která se používá k odpovědi.</span><span class="sxs-lookup"><span data-stu-id="04a43-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="04a43-110">[out] Vyrovnávací paměť s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="04a43-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04a43-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04a43-111">Remarks</span></span>  
 <span data-ttu-id="04a43-112">`Request` Metoda usnadňuje přidání neurčené vlastní operace.</span><span class="sxs-lookup"><span data-stu-id="04a43-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="04a43-113">To znamená tato metoda zajišťuje rozšiřitelnost bez nutnosti revizi definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04a43-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="04a43-114">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="04a43-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a43-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04a43-115">Requirements</span></span>  
 <span data-ttu-id="04a43-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a43-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a43-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="04a43-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="04a43-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04a43-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04a43-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a43-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a43-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="04a43-120">See Also</span></span>  
 [<span data-ttu-id="04a43-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a43-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
