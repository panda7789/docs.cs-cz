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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f42345977f69dd27294a44b4c007ab08d2ec6f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468348"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="4a7be-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="4a7be-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="4a7be-103">[Podporované v [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="4a7be-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="4a7be-104">Přečte bajtů ze symbolů v paměti datového proudu.</span><span class="sxs-lookup"><span data-stu-id="4a7be-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a7be-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a7be-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a7be-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4a7be-107">[in] Identifikátor modulu, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="4a7be-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="4a7be-108">[in] Posun v rámci datového proudu v paměti od kterého začne číst bajty.</span><span class="sxs-lookup"><span data-stu-id="4a7be-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="4a7be-109">[out] Ukazatel do vyrovnávací paměti, do které se kopírují data.</span><span class="sxs-lookup"><span data-stu-id="4a7be-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="4a7be-110">Vyrovnávací paměť by měl mít `countSymbolBytes` volného místa.</span><span class="sxs-lookup"><span data-stu-id="4a7be-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="4a7be-111">[in] Počet bajtů, které mají kopírovat.</span><span class="sxs-lookup"><span data-stu-id="4a7be-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="4a7be-112">[out] Po návratu metody obsahuje skutečný počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="4a7be-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a7be-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a7be-113">Return Value</span></span>  
 <span data-ttu-id="4a7be-114">`S_OK`, pokud byla přečtena nenulové počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="4a7be-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="4a7be-115">`CORPROF_E_MODULE_IS_DYNAMIC`, pokud modul byl vytvořen pomocí <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="4a7be-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a7be-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a7be-116">Remarks</span></span>  
 <span data-ttu-id="4a7be-117">`ReadInMemorySymbols` Metoda se pokusí přečíst `countSymbolBytes` dat začínající na posunu `symbolsReadOffset` v rámci datového proudu v paměti.</span><span class="sxs-lookup"><span data-stu-id="4a7be-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="4a7be-118">Data zkopírována do `pSymbolBytes`, která má mít `countSymbolBytes` volného místa.</span><span class="sxs-lookup"><span data-stu-id="4a7be-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="4a7be-119">`pCountSymbolsBytesRead` obsahuje skutečný počet bajtů, přečtěte si, které mohou být menší než `countSymbolBytes` Pokud je dosaženo konce datového proudu.</span><span class="sxs-lookup"><span data-stu-id="4a7be-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a7be-120">Aktuální implementace nepodporuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="4a7be-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="4a7be-121">Pokud modul byl vytvořen pomocí třídy Reflection.Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="4a7be-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a7be-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a7be-122">Requirements</span></span>  
 <span data-ttu-id="4a7be-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a7be-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a7be-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a7be-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a7be-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a7be-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a7be-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a7be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7be-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a7be-127">See also</span></span>
- [<span data-ttu-id="4a7be-128">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a7be-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
