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
ms.openlocfilehash: b913affb4728dc80ba67438384cbeac87265f76d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860536"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="f29ee-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="f29ee-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="f29ee-103">Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.</span><span class="sxs-lookup"><span data-stu-id="f29ee-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f29ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f29ee-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f29ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f29ee-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="f29ee-106">pro Definováno uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f29ee-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="f29ee-107">pro Velikost vstupní vyrovnávací paměti, která se používá pro příchozí požadavek.</span><span class="sxs-lookup"><span data-stu-id="f29ee-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="f29ee-108">pro Vyrovnávací paměť obsahující požadavek.</span><span class="sxs-lookup"><span data-stu-id="f29ee-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="f29ee-109">pro Velikost výstupní vyrovnávací paměti, která se používá pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="f29ee-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="f29ee-110">mimo Vyrovnávací paměť obsahující odpověď.</span><span class="sxs-lookup"><span data-stu-id="f29ee-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f29ee-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f29ee-111">Remarks</span></span>  
 <span data-ttu-id="f29ee-112">`Request` Metoda usnadňuje přidání nespecifikovaných vlastních operací.</span><span class="sxs-lookup"><span data-stu-id="f29ee-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="f29ee-113">To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti Revize definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f29ee-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="f29ee-114">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f29ee-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f29ee-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f29ee-115">Requirements</span></span>  
 <span data-ttu-id="f29ee-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f29ee-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29ee-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f29ee-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f29ee-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f29ee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f29ee-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29ee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f29ee-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f29ee-120">See also</span></span>

- [<span data-ttu-id="f29ee-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f29ee-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
