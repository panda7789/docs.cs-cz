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
ms.openlocfilehash: 0332fae46d6a65cfb7cc0b929cc2fd0d97e1790e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179149"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="3c57f-102">ICLRDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="3c57f-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="3c57f-103">Přečte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3c57f-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c57f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c57f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c57f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c57f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3c57f-106">[v] CLRDATA_ADDRESS, který ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="3c57f-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="3c57f-107">[out] Ukazatel na vyrovnávací paměť, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="3c57f-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="3c57f-108">[v] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3c57f-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="3c57f-109">[out] Ukazatel na počet vrácených bajtů.</span><span class="sxs-lookup"><span data-stu-id="3c57f-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c57f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c57f-110">Requirements</span></span>  
 <span data-ttu-id="3c57f-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c57f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c57f-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3c57f-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3c57f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c57f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c57f-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c57f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c57f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c57f-115">See also</span></span>

- [<span data-ttu-id="3c57f-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c57f-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
