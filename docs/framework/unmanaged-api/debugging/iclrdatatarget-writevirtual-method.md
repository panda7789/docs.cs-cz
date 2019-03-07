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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1d9fdef9d183a03fd7f335a13683e1d1a3f95c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485717"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="e6dcb-102">ICLRDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="e6dcb-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="e6dcb-103">Zapisuje data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="e6dcb-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6dcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dcb-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6dcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6dcb-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e6dcb-106">[in] CLRDATA_ADDRESS, která ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="e6dcb-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e6dcb-107">[in] Ukazatel do vyrovnávací paměti, která ukládá data, která má být proveden zápis.</span><span class="sxs-lookup"><span data-stu-id="e6dcb-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="e6dcb-108">[in] Počet bajtů, které mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="e6dcb-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="e6dcb-109">[out] Ukazatel na skutečný počet bajtů, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="e6dcb-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6dcb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6dcb-110">Requirements</span></span>  
 <span data-ttu-id="e6dcb-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6dcb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6dcb-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e6dcb-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e6dcb-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6dcb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6dcb-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6dcb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dcb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6dcb-115">See also</span></span>
- [<span data-ttu-id="e6dcb-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6dcb-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
