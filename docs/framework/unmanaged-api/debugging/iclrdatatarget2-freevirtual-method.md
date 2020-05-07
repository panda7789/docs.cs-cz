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
ms.openlocfilehash: 0a36af5b411673081e74aa243ec8e0f8f876f238
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860482"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="7c89f-102">ICLRDataTarget2::FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7c89f-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="7c89f-103">Volána službami CLR (Common Language Runtime) pro přístup k datům k uvolnění paměti, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="7c89f-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c89f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c89f-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c89f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c89f-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="7c89f-106">pro `CLRDATA_ADDRESS` Hodnota, která určuje počáteční adresu paměti, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7c89f-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="7c89f-107">pro Velikost paměti, která se má uvolnit (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="7c89f-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="7c89f-108">pro Příznaky, které řídí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7c89f-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="7c89f-109">Podívejte se na `VirtualFree` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="7c89f-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c89f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c89f-110">Remarks</span></span>  
 <span data-ttu-id="7c89f-111">`FreeVirtual` Metoda slouží jako logická obálka funkce Win32 `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="7c89f-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="7c89f-112">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c89f-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c89f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c89f-113">Requirements</span></span>  
 <span data-ttu-id="7c89f-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c89f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c89f-115">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7c89f-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7c89f-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7c89f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c89f-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c89f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c89f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c89f-118">See also</span></span>

- [<span data-ttu-id="7c89f-119">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c89f-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="7c89f-120">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7c89f-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
