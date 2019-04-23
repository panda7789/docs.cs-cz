---
title: ICLRDataTarget::ReadVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e2ec063d46ce9c890927391107888032e31378
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092592"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="bb0d2-102">ICLRDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="bb0d2-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="bb0d2-103">Načte data z adresy zadaná virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bb0d2-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb0d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb0d2-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb0d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb0d2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bb0d2-106">[in] CLRDATA_ADDRESS, která ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="bb0d2-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="bb0d2-107">[out] Ukazatel do vyrovnávací paměti, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="bb0d2-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="bb0d2-108">[in] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bb0d2-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="bb0d2-109">[out] Ukazatel na počet bajtů vrácených.</span><span class="sxs-lookup"><span data-stu-id="bb0d2-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb0d2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb0d2-110">Requirements</span></span>  
 <span data-ttu-id="bb0d2-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb0d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb0d2-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="bb0d2-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bb0d2-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb0d2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb0d2-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb0d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0d2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb0d2-115">See also</span></span>

- [<span data-ttu-id="bb0d2-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb0d2-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
