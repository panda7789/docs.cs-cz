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
ms.openlocfilehash: 4a0beb9a0b1ef2db6ff32fee1b55b3478794509a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219730"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="82520-102">ICLRDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="82520-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="82520-103">Zapisuje data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="82520-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82520-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82520-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82520-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82520-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="82520-106">[in] CLRDATA_ADDRESS, která ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="82520-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="82520-107">[in] Ukazatel do vyrovnávací paměti, která ukládá data, která má být proveden zápis.</span><span class="sxs-lookup"><span data-stu-id="82520-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="82520-108">[in] Počet bajtů, které mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="82520-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="82520-109">[out] Ukazatel na skutečný počet bajtů, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="82520-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82520-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82520-110">Requirements</span></span>  
 <span data-ttu-id="82520-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82520-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82520-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="82520-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="82520-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82520-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="82520-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="82520-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="82520-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82520-115">See also</span></span>

- [<span data-ttu-id="82520-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82520-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
