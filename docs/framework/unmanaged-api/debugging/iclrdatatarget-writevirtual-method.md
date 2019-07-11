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
ms.openlocfilehash: a0ad4b7e907412aced911d7869ffce81eb867448
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738517"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="ad321-102">ICLRDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="ad321-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="ad321-103">Zapisuje data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ad321-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad321-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad321-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad321-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad321-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ad321-106">[in] CLRDATA_ADDRESS, která ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ad321-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="ad321-107">[in] Ukazatel do vyrovnávací paměti, která ukládá data, která má být proveden zápis.</span><span class="sxs-lookup"><span data-stu-id="ad321-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="ad321-108">[in] Počet bajtů, které mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="ad321-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="ad321-109">[out] Ukazatel na skutečný počet bajtů, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="ad321-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad321-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad321-110">Requirements</span></span>  
 <span data-ttu-id="ad321-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad321-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad321-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ad321-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad321-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad321-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad321-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad321-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad321-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad321-115">See also</span></span>

- [<span data-ttu-id="ad321-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad321-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
