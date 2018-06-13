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
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455928"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="3d126-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="3d126-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="3d126-103">[V podporované [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]</span><span class="sxs-lookup"><span data-stu-id="3d126-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="3d126-104">Čte bajtů z datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="3d126-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d126-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d126-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d126-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d126-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3d126-107">[v] Identifikátor modul, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="3d126-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="3d126-108">[v] Posun v rámci datového proudu v paměti, pro kterou chcete spustit čtení bajtů.</span><span class="sxs-lookup"><span data-stu-id="3d126-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="3d126-109">[out] Ukazatel do vyrovnávací paměti, ke kterému se zkopírují data.</span><span class="sxs-lookup"><span data-stu-id="3d126-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="3d126-110">Vyrovnávací paměti by měl mít `countSymbolBytes` množství dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="3d126-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="3d126-111">[v] Počet bajtů ke kopírování.</span><span class="sxs-lookup"><span data-stu-id="3d126-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="3d126-112">[out] Po návratu metody obsahuje skutečný počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="3d126-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d126-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3d126-113">Return Value</span></span>  
 <span data-ttu-id="3d126-114">`S_OK`, pokud byla přečtena nenulový počet bajtů.</span><span class="sxs-lookup"><span data-stu-id="3d126-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="3d126-115">`CORPROF_E_MODULE_IS_DYNAMIC`, pokud modul byl vytvořen pomocí <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="3d126-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d126-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d126-116">Remarks</span></span>  
 <span data-ttu-id="3d126-117">`ReadInMemorySymbols` Metoda se pokusí přečíst `countSymbolBytes` začínající na posunu dat `symbolsReadOffset` v rámci datového proudu v paměti.</span><span class="sxs-lookup"><span data-stu-id="3d126-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="3d126-118">Data budou zkopírována do `pSymbolBytes`, který by měl být `countSymbolBytes` množství dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="3d126-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="3d126-119">`pCountSymbolsBytesRead` obsahuje skutečný počet bajtů přečtených, což může být menší než `countSymbolBytes` Pokud dosažen konec datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3d126-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d126-120">Aktuální implementace Reflection.Emit nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="3d126-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="3d126-121">Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="3d126-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d126-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d126-122">Requirements</span></span>  
 <span data-ttu-id="3d126-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d126-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d126-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d126-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d126-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d126-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d126-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d126-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d126-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d126-127">See Also</span></span>  
 [<span data-ttu-id="3d126-128">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d126-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
