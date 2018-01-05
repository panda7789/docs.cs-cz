---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type: COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5851f73cc899ef21d8a5dcfd8f03617641a6625a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="dc454-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="dc454-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="dc454-103">[V podporované [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="dc454-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="dc454-104">Čte bajtů z datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="dc454-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc454-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc454-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc454-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc454-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="dc454-107">[v] Identifikátor modul, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="dc454-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="dc454-108">[v] Posun v rámci datového proudu v paměti, pro kterou chcete spustit čtení bajtů.</span><span class="sxs-lookup"><span data-stu-id="dc454-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="dc454-109">[out] Ukazatel do vyrovnávací paměti, ke kterému se zkopírují data.</span><span class="sxs-lookup"><span data-stu-id="dc454-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="dc454-110">Vyrovnávací paměti by měl mít `countSymbolBytes` množství dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="dc454-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="dc454-111">[v] Počet bajtů ke kopírování.</span><span class="sxs-lookup"><span data-stu-id="dc454-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="dc454-112">[out] Po návratu metody obsahuje skutečný počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="dc454-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc454-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc454-113">Return Value</span></span>  
 <span data-ttu-id="dc454-114">`S_OK`, pokud byla přečtena nenulový počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="dc454-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="dc454-115">`CORPROF_E_MODULE_IS_DYNAMIC`, pokud modul byl vytvořen pomocí <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="dc454-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc454-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc454-116">Remarks</span></span>  
 <span data-ttu-id="dc454-117">`ReadInMemorySymbols` Metoda se pokusí přečíst `countSymbolBytes` začínající na posunu dat `symbolsReadOffset` v rámci datového proudu v paměti.</span><span class="sxs-lookup"><span data-stu-id="dc454-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="dc454-118">Data budou zkopírována do `pSymbolBytes`, který by měl být `countSymbolBytes` množství dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="dc454-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="dc454-119">`pCountSymbolsBytesRead`obsahuje skutečný počet bajtů přečtených, což může být menší než `countSymbolBytes` Pokud dosažen konec datového proudu.</span><span class="sxs-lookup"><span data-stu-id="dc454-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc454-120">Aktuální implementace Reflection.Emit nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="dc454-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="dc454-121">Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="dc454-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc454-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc454-122">Requirements</span></span>  
 <span data-ttu-id="dc454-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc454-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc454-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc454-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc454-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc454-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc454-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc454-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc454-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc454-127">See Also</span></span>  
 [<span data-ttu-id="dc454-128">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc454-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
