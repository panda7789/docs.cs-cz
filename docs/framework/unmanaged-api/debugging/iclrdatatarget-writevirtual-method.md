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
ms.openlocfilehash: 6a7a7736837f7e6bbf1ad4982e78a75550abbeab
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860499"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="452a5-102">ICLRDataTarget::WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="452a5-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="452a5-103">Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="452a5-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="452a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="452a5-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="452a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="452a5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="452a5-106">pro CLRDATA_ADDRESS, který ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="452a5-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="452a5-107">pro Ukazatel na vyrovnávací paměť, ve kterém jsou uložena data, která mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="452a5-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="452a5-108">pro Počet bajtů, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="452a5-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="452a5-109">mimo Ukazatel na skutečný počet zapsaných bajtů.</span><span class="sxs-lookup"><span data-stu-id="452a5-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="452a5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="452a5-110">Requirements</span></span>  
 <span data-ttu-id="452a5-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="452a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="452a5-112">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="452a5-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="452a5-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="452a5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="452a5-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="452a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452a5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="452a5-115">See also</span></span>

- [<span data-ttu-id="452a5-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="452a5-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
