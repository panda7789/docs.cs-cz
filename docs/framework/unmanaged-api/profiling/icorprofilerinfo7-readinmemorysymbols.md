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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868340"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="a05ca-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="a05ca-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="a05ca-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="a05ca-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a05ca-104">Načte bajty z datového proudu symbolů v paměti.</span><span class="sxs-lookup"><span data-stu-id="a05ca-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a05ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a05ca-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a05ca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a05ca-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a05ca-107">pro Identifikátor modulu, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="a05ca-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="a05ca-108">pro Posun v rámci proudu v paměti, ve kterém se mají začít číst bajty.</span><span class="sxs-lookup"><span data-stu-id="a05ca-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="a05ca-109">mimo Ukazatel na vyrovnávací paměť, do které budou kopírována data.</span><span class="sxs-lookup"><span data-stu-id="a05ca-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="a05ca-110">Vyrovnávací paměť by měla mít `countSymbolBytes` dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="a05ca-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="a05ca-111">pro Počet bajtů, které mají být zkopírovány.</span><span class="sxs-lookup"><span data-stu-id="a05ca-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="a05ca-112">mimo Když metoda vrátí, obsahuje skutečný počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="a05ca-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a05ca-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a05ca-113">Return Value</span></span>  
 <span data-ttu-id="a05ca-114">`S_OK`, pokud byl přečten nenulový počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="a05ca-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="a05ca-115">`CORPROF_E_MODULE_IS_DYNAMIC`, pokud byl modul vytvořen pomocí <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a05ca-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a05ca-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a05ca-116">Remarks</span></span>  
 <span data-ttu-id="a05ca-117">Metoda `ReadInMemorySymbols` se pokusí přečíst `countSymbolBytes` dat počínaje posunem `symbolsReadOffset` v datovém proudu v paměti.</span><span class="sxs-lookup"><span data-stu-id="a05ca-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="a05ca-118">Data se zkopírují do `pSymbolBytes`, u kterých se očekává `countSymbolBytes` dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="a05ca-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="a05ca-119">`pCountSymbolsBytesRead` obsahuje skutečný počet přečtených bajtů, který může být menší než `countSymbolBytes`, pokud je dosaženo konce datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a05ca-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a05ca-120">Aktuální implementace nepodporuje reflexe. Emit.</span><span class="sxs-lookup"><span data-stu-id="a05ca-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="a05ca-121">Pokud byl modul vytvořen pomocí reflexe. Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="a05ca-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a05ca-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a05ca-122">Requirements</span></span>  
 <span data-ttu-id="a05ca-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a05ca-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a05ca-124">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a05ca-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a05ca-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a05ca-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a05ca-126">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a05ca-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ca-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a05ca-127">See also</span></span>

- [<span data-ttu-id="a05ca-128">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a05ca-128">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
