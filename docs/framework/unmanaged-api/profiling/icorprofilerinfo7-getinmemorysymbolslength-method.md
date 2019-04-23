---
title: ICorProfilerInfo7::GetInMemorySymbolsLength Method
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422fdfef6bea40e0f4bcc7447df8dba1eab2896e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146091"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="8c3a7-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span><span class="sxs-lookup"><span data-stu-id="8c3a7-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="8c3a7-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="8c3a7-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8c3a7-104">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c3a7-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c3a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c3a7-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8c3a7-107">[in] Identifikátor modulu, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="8c3a7-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="8c3a7-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="8c3a7-109">[out] Ukazatel `DWORD` hodnotu, která po návratu metody obsahuje délku datového proudu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c3a7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c3a7-110">Return Value</span></span>  
 <span data-ttu-id="8c3a7-111">Metoda vrátí `S_OK` Pokud nelze určit délka datového proudu paměti, i když je nula (0).</span><span class="sxs-lookup"><span data-stu-id="8c3a7-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="8c3a7-112">Metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC` Pokud metoda byl vytvořen pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c3a7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c3a7-113">Remarks</span></span>  
 <span data-ttu-id="8c3a7-114">Pokud ho modul obsahuje symboly v paměti, délku datového proudu je umístěn v `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="8c3a7-115">Pokud modul nemá symboly v paměti `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c3a7-116">Aktuální implementace nepodporuje Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="8c3a7-117">Pokud modul byl vytvořen pomocí třídy Reflection.Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="8c3a7-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c3a7-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c3a7-118">Requirements</span></span>  
 <span data-ttu-id="8c3a7-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3a7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3a7-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c3a7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c3a7-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c3a7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c3a7-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3a7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3a7-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c3a7-123">See also</span></span>

- [<span data-ttu-id="8c3a7-124">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c3a7-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
