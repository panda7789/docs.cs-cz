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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179115"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="2c276-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="2c276-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="2c276-103">Volat služby přístupu k datům cltime společného jazyka (CLR) požádat o operaci, jak je definováno implementací.</span><span class="sxs-lookup"><span data-stu-id="2c276-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c276-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c276-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="2c276-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c276-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="2c276-106">[v] Definováno uživatelem.</span><span class="sxs-lookup"><span data-stu-id="2c276-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="2c276-107">[v] Velikost vstupní vyrovnávací paměti, která se používá pro příchozí požadavek.</span><span class="sxs-lookup"><span data-stu-id="2c276-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="2c276-108">[v] Vyrovnávací paměť obsahující požadavek.</span><span class="sxs-lookup"><span data-stu-id="2c276-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="2c276-109">[v] Velikost výstupní vyrovnávací paměti, která se používá pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="2c276-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="2c276-110">[out] A Buffer obsahující odpověď.</span><span class="sxs-lookup"><span data-stu-id="2c276-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c276-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c276-111">Remarks</span></span>  
 <span data-ttu-id="2c276-112">Metoda `Request` usnadňuje přidání nespecifikovaných vlastních operací.</span><span class="sxs-lookup"><span data-stu-id="2c276-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="2c276-113">To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti revize definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2c276-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="2c276-114">Tato metoda je implementována zapisovače ladicí aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c276-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c276-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c276-115">Requirements</span></span>  
 <span data-ttu-id="2c276-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c276-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c276-117">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2c276-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2c276-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c276-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c276-119">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c276-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c276-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c276-120">See also</span></span>

- [<span data-ttu-id="2c276-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c276-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
