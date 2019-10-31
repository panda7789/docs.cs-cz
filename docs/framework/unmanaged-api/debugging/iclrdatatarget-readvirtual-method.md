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
ms.openlocfilehash: 0c26a2df3f73af5ebd1f8b735d7662bb23ba4228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134165"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="bf7a6-102">ICLRDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="bf7a6-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="bf7a6-103">Načte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bf7a6-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf7a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf7a6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf7a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf7a6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="bf7a6-106">pro CLRDATA_ADDRESS, který ukládá adresu virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="bf7a6-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="bf7a6-107">mimo Ukazatel na vyrovnávací paměť, která přijímá data.</span><span class="sxs-lookup"><span data-stu-id="bf7a6-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="bf7a6-108">pro Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bf7a6-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="bf7a6-109">mimo Ukazatel na počet vrácených bajtů.</span><span class="sxs-lookup"><span data-stu-id="bf7a6-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf7a6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf7a6-110">Requirements</span></span>  
 <span data-ttu-id="bf7a6-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf7a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf7a6-112">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="bf7a6-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bf7a6-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bf7a6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf7a6-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf7a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf7a6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf7a6-115">See also</span></span>

- [<span data-ttu-id="bf7a6-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf7a6-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
