---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: e4fa0a3745200d39a468292e9520b1aeb0e9f1b2
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860678"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="795e1-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="795e1-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="795e1-103">Volá se [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) , aby se do ladicího programu nahlásila výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="795e1-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="795e1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="795e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="795e1-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="795e1-106">pro Počáteční adresa oblasti paměti, ve které se má vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="795e1-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="795e1-107">pro Velikost oblasti paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="795e1-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="795e1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="795e1-108">Remarks</span></span>  
 <span data-ttu-id="795e1-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Metoda po každém pokusu o výčet oblasti paměti zavolá tuto metodu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="795e1-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="795e1-110">Výčet bude pokračovat i v případě, že tato metoda vrátí hodnotu HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="795e1-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="795e1-111">Oblasti hlášené tímto zpětným voláním můžou být duplicitní nebo překrývající se oblasti.</span><span class="sxs-lookup"><span data-stu-id="795e1-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795e1-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="795e1-112">Requirements</span></span>  
 <span data-ttu-id="795e1-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="795e1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="795e1-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="795e1-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="795e1-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="795e1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="795e1-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="795e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795e1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="795e1-117">See also</span></span>

- [<span data-ttu-id="795e1-118">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="795e1-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
