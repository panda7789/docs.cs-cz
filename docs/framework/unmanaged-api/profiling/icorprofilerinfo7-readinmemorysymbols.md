---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: ae51490be96f3eb6524831c93739c3befbc30b37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132028"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="252f6-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="252f6-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="252f6-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="252f6-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="252f6-104">Načte bajty z datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="252f6-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="252f6-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="252f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="252f6-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="252f6-107">pro Identifikátor modulu, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="252f6-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="252f6-108">pro Posun v rámci proudu v paměti, ve kterém se mají začít číst bajty.</span><span class="sxs-lookup"><span data-stu-id="252f6-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="252f6-109">mimo Ukazatel na vyrovnávací paměť, do které budou kopírována data.</span><span class="sxs-lookup"><span data-stu-id="252f6-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="252f6-110">Vyrovnávací paměť by měla mít `countSymbolBytes` dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="252f6-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="252f6-111">pro Počet bajtů, které mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="252f6-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="252f6-112">mimo Když metoda vrátí, obsahuje skutečný počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="252f6-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="252f6-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="252f6-113">Return Value</span></span>  
 <span data-ttu-id="252f6-114">`S_OK`, pokud byl přečten nenulový počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="252f6-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="252f6-115">`CORPROF_E_MODULE_IS_DYNAMIC`, pokud byl modul vytvořen pomocí <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="252f6-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="252f6-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="252f6-116">Remarks</span></span>  
 <span data-ttu-id="252f6-117">Metoda `ReadInMemorySymbols` se pokusí přečíst `countSymbolBytes` dat počínaje posunem `symbolsReadOffset` v datovém proudu v paměti.</span><span class="sxs-lookup"><span data-stu-id="252f6-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="252f6-118">Data se zkopírují do `pSymbolBytes`, u kterých se očekává `countSymbolBytes` dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="252f6-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="252f6-119">`pCountSymbolsBytesRead` obsahuje skutečný počet přečtených bajtů, který může být menší než `countSymbolBytes`, pokud je dosaženo konce datového proudu.</span><span class="sxs-lookup"><span data-stu-id="252f6-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="252f6-120">Aktuální implementace nepodporuje reflexe. Emit.</span><span class="sxs-lookup"><span data-stu-id="252f6-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="252f6-121">Pokud byl modul vytvořen pomocí reflexe. Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="252f6-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="252f6-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="252f6-122">Requirements</span></span>  
 <span data-ttu-id="252f6-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="252f6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="252f6-124">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="252f6-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="252f6-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="252f6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="252f6-126">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="252f6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="252f6-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="252f6-127">See also</span></span>

- [<span data-ttu-id="252f6-128">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="252f6-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
