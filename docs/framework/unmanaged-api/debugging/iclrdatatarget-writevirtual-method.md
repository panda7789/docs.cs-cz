---
title: ICLRDataTarget::WriteVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: bd2f67c2d7230d3873b4dc0df73ac1be778a0828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179100"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="c2c54-102">ICLRDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c2c54-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="c2c54-103">Zapíše data ze zadané vyrovnávací paměti na zadanou adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c2c54-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2c54-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2c54-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="c2c54-106">[v] CLRDATA_ADDRESS, který ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c2c54-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c2c54-107">[v] Ukazatel na vyrovnávací paměť, která ukládá data, která mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="c2c54-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="c2c54-108">[v] Počet bajtů, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="c2c54-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="c2c54-109">[out] Ukazatel na skutečný počet zapsaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="c2c54-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c54-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2c54-110">Requirements</span></span>  
 <span data-ttu-id="c2c54-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c54-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c54-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c2c54-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c2c54-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2c54-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c54-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c54-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2c54-115">See also</span></span>

- [<span data-ttu-id="c2c54-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2c54-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
