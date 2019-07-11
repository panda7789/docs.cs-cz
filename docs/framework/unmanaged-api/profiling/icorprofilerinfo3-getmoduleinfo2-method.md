---
title: ICorProfilerInfo3::GetModuleInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ead38d54d470c3f443ae5e27e4a2d045bc27c79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783038"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="1d8df-102">ICorProfilerInfo3::GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="1d8df-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="1d8df-103">Dané ID modulu vrátí název souboru modulu, ID modulu nadřazené sestavení a bitová maska, která popisuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d8df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d8df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d8df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d8df-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1d8df-106">[in] ID modulu, pro kterou budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="1d8df-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="1d8df-107">[out] Základní adresa, načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1d8df-108">[in] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1d8df-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1d8df-109">[out] Celkový počet znaků z modulů název souboru, který je vrácen ukazatel.</span><span class="sxs-lookup"><span data-stu-id="1d8df-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d8df-110">[out] Pokud volající širokého znaku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1d8df-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="1d8df-111">Po návratu metody obsahuje tuto vyrovnávací paměť názvu souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="1d8df-112">[out] Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="1d8df-113">[out] Bitová maska hodnot z [cor_prf_module_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) výčet, který určit vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d8df-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d8df-114">Remarks</span></span>  
 <span data-ttu-id="1d8df-115">Pro dynamické moduly `szName` parametr je název metadata modulu a základní adresa je 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="1d8df-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="1d8df-116">Název metadat je hodnota ve sloupci název z tabulky modulu uvnitř metadat.</span><span class="sxs-lookup"><span data-stu-id="1d8df-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="1d8df-117">To je také vystavena jako <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> vlastnost do spravovaného kódu a jako `szName` parametr [imetadataimport::getscopeprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) metodu pro nespravované metadat klientský kód.</span><span class="sxs-lookup"><span data-stu-id="1d8df-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="1d8df-118">I když `GetModuleInfo2` metoda může být volána jako ID modulu existuje, ID nadřazeného sestavení nebude k dispozici, dokud profiler obdrží [icorprofilercallback::moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1d8df-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="1d8df-119">Když `GetModuleInfo2` vrátí, musíte ověřit, že `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="1d8df-120">K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="1d8df-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1d8df-121">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetModuleInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="1d8df-122">Alternativně můžete nejprve volat `GetModuleInfo2` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="1d8df-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1d8df-123">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetModuleInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="1d8df-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d8df-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d8df-124">Requirements</span></span>  
 <span data-ttu-id="1d8df-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d8df-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d8df-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d8df-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d8df-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d8df-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d8df-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d8df-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8df-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d8df-129">See also</span></span>

- [<span data-ttu-id="1d8df-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d8df-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1d8df-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1d8df-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1d8df-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="1d8df-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
