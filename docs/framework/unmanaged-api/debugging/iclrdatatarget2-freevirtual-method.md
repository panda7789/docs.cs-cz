---
title: ICLRDataTarget2::FreeVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793662"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="caec8-102">ICLRDataTarget2::FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="caec8-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="caec8-103">Volána službami CLR (Common Language Runtime) pro přístup k datům k uvolnění paměti, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="caec8-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caec8-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caec8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caec8-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="caec8-106">pro Hodnota `CLRDATA_ADDRESS`, která určuje počáteční adresu paměti, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="caec8-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="caec8-107">pro Velikost paměti, která se má uvolnit (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="caec8-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="caec8-108">pro Příznaky, které řídí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="caec8-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="caec8-109">Podívejte se na funkci Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="caec8-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caec8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="caec8-110">Remarks</span></span>  
 <span data-ttu-id="caec8-111">Metoda `FreeVirtual` slouží jako logická obálka funkce Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="caec8-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="caec8-112">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="caec8-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caec8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caec8-113">Requirements</span></span>  
 <span data-ttu-id="caec8-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caec8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caec8-115">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="caec8-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="caec8-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="caec8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caec8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caec8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caec8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caec8-118">See also</span></span>

- [<span data-ttu-id="caec8-119">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caec8-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="caec8-120">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="caec8-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
