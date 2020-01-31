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
ms.openlocfilehash: c8313b7c97eb5d94424259dc91459f62e13368fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785597"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="49b2d-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="49b2d-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="49b2d-103">Volá se [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) , aby se do ladicího programu nahlásila výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="49b2d-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49b2d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49b2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49b2d-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="49b2d-106">pro Počáteční adresa oblasti paměti, ve které se má vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="49b2d-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="49b2d-107">pro Velikost oblasti paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="49b2d-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49b2d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49b2d-108">Remarks</span></span>  
 <span data-ttu-id="49b2d-109">Metoda `ICLRDataEnumMemoryRegions::EnumMemoryRegions` vyvolá tuto metodu zpětného volání po každém pokusu o vytvoření výčtu oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="49b2d-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="49b2d-110">Výčet bude pokračovat i v případě, že tato metoda vrátí hodnotu HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="49b2d-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="49b2d-111">Oblasti hlášené tímto zpětným voláním můžou být duplicitní nebo překrývající se oblasti.</span><span class="sxs-lookup"><span data-stu-id="49b2d-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49b2d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49b2d-112">Requirements</span></span>  
 <span data-ttu-id="49b2d-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49b2d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49b2d-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="49b2d-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="49b2d-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49b2d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49b2d-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49b2d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b2d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49b2d-117">See also</span></span>

- [<span data-ttu-id="49b2d-118">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49b2d-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
