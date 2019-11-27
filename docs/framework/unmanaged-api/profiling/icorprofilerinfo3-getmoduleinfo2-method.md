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
ms.openlocfilehash: e2a4df262e076c960640977bea0d22be19802140
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449665"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="09962-102">ICorProfilerInfo3::GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="09962-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="09962-103">Po předaném ID modulu vrátí název souboru modulu, ID nadřazeného sestavení modulu a bitovou masku, která popisuje vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="09962-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09962-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09962-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="09962-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09962-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="09962-106">pro ID modulu, pro který budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="09962-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="09962-107">mimo Základní adresa, na které je modul načten.</span><span class="sxs-lookup"><span data-stu-id="09962-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="09962-108">pro Délka `szName` návratové vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="09962-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="09962-109">mimo Ukazatel na celkovou délku znaku v názvu souboru modulu, který je vrácen.</span><span class="sxs-lookup"><span data-stu-id="09962-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="09962-110">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="09962-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="09962-111">Když se metoda vrátí, tato vyrovnávací paměť obsahuje název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="09962-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="09962-112">mimo Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="09962-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="09962-113">mimo Bitová maska hodnot z výčtu [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) , které určují vlastnosti modulu.</span><span class="sxs-lookup"><span data-stu-id="09962-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09962-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09962-114">Remarks</span></span>  
 <span data-ttu-id="09962-115">Pro dynamické moduly je parametr `szName` názvem metadat modulu a základní adresa je 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="09962-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="09962-116">Název metadat je hodnota ve sloupci název z tabulky modulů v metadatech.</span><span class="sxs-lookup"><span data-stu-id="09962-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="09962-117">To je také zveřejněné jako vlastnost <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> pro spravovaný kód a jako parametr `szName` metody [IMetaDataImport:: GetScopeProps –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) na nespravovaný kód klienta metadat.</span><span class="sxs-lookup"><span data-stu-id="09962-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="09962-118">I když může být metoda `GetModuleInfo2` volána, jakmile existuje ID modulu, ID nadřazeného sestavení nebude k dispozici, dokud Profiler neobdrží zpětné volání [ICorProfilerCallback:: ModuleAttachedToAssembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09962-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="09962-119">Když `GetModuleInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="09962-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="09962-120">To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="09962-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="09962-121">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetModuleInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="09962-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="09962-122">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetModuleInfo2` s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="09962-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="09962-123">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetModuleInfo2` znovu.</span><span class="sxs-lookup"><span data-stu-id="09962-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09962-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09962-124">Requirements</span></span>  
 <span data-ttu-id="09962-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09962-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09962-126">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="09962-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09962-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09962-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09962-128">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09962-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09962-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09962-129">See also</span></span>

- [<span data-ttu-id="09962-130">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09962-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="09962-131">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="09962-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="09962-132">Profilace</span><span class="sxs-lookup"><span data-stu-id="09962-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
