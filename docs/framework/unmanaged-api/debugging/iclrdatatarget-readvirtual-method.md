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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698093"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="9c2f9-102">ICLRDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="9c2f9-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="9c2f9-103">Načte data z adresy zadaná virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9c2f9-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c2f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c2f9-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c2f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c2f9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9c2f9-106">[in] CLRDATA_ADDRESS, která ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="9c2f9-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9c2f9-107">[out] Ukazatel do vyrovnávací paměti, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="9c2f9-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="9c2f9-108">[in] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9c2f9-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="9c2f9-109">[out] Ukazatel na počet bajtů vrácených.</span><span class="sxs-lookup"><span data-stu-id="9c2f9-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c2f9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c2f9-110">Requirements</span></span>  
 <span data-ttu-id="9c2f9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c2f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c2f9-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9c2f9-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9c2f9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c2f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c2f9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c2f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2f9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c2f9-115">See also</span></span>

- [<span data-ttu-id="9c2f9-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c2f9-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
