---
title: ICLRDataTarget2::AllocVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789090"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="225e8-102">ICLRDataTarget2::AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="225e8-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="225e8-103">Volá se službami CLR (Common Language Runtime) k přidělení paměti v adresním prostoru tohoto cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="225e8-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="225e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="225e8-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="225e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="225e8-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="225e8-106">pro Hodnota `CLRDATA_ADDRESS`, která určuje požadovanou počáteční adresu paměti, která má být přidělena.</span><span class="sxs-lookup"><span data-stu-id="225e8-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="225e8-107">pro Velikost paměti, která se má přidělit (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="225e8-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="225e8-108">pro Příznaky, které řídí přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="225e8-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="225e8-109">Podívejte se na funkci Win32 `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="225e8-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="225e8-110">pro Atributy ochrany přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="225e8-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="225e8-111">Podívejte se na funkci Win32 `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="225e8-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="225e8-112">mimo Ukazatel na hodnotu `CLRDATA_ADDRESS`, která určuje skutečnou počáteční adresu přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="225e8-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="225e8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="225e8-113">Remarks</span></span>  
 <span data-ttu-id="225e8-114">Metoda `AllocVirtual` slouží jako logická obálka funkce Win32 `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="225e8-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="225e8-115">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="225e8-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225e8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="225e8-116">Requirements</span></span>  
 <span data-ttu-id="225e8-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="225e8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225e8-118">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="225e8-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="225e8-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="225e8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="225e8-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225e8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225e8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="225e8-121">See also</span></span>

- [<span data-ttu-id="225e8-122">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="225e8-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="225e8-123">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="225e8-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
