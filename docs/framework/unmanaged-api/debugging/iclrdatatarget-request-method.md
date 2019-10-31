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
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113355"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="0b677-102">ICLRDataTarget::Request – metoda</span><span class="sxs-lookup"><span data-stu-id="0b677-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="0b677-103">Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.</span><span class="sxs-lookup"><span data-stu-id="0b677-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b677-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b677-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0b677-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b677-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="0b677-106">pro Definováno uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0b677-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="0b677-107">pro Velikost vstupní vyrovnávací paměti, která se používá pro příchozí požadavek.</span><span class="sxs-lookup"><span data-stu-id="0b677-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="0b677-108">pro Vyrovnávací paměť obsahující požadavek.</span><span class="sxs-lookup"><span data-stu-id="0b677-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="0b677-109">pro Velikost výstupní vyrovnávací paměti, která se používá pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="0b677-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="0b677-110">mimo Vyrovnávací paměť obsahující odpověď.</span><span class="sxs-lookup"><span data-stu-id="0b677-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b677-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b677-111">Remarks</span></span>  
 <span data-ttu-id="0b677-112">Metoda `Request` usnadňuje přidání nespecifikovaných vlastních operací.</span><span class="sxs-lookup"><span data-stu-id="0b677-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="0b677-113">To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti Revize definice rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0b677-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="0b677-114">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b677-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b677-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b677-115">Requirements</span></span>  
 <span data-ttu-id="0b677-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b677-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b677-117">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0b677-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0b677-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b677-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b677-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b677-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b677-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b677-120">See also</span></span>

- [<span data-ttu-id="0b677-121">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b677-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
