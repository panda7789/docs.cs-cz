---
title: ICorProfilerInfo::GetModuleInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 25c5568e4cae0ead82b59b09dbbb9a11e4bc2df2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863436"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="cacbf-102">ICorProfilerInfo::GetModuleInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cacbf-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="cacbf-103">Po předaném ID modulu vrátí název souboru modulu a ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cacbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cacbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cacbf-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="cacbf-106">pro ID modulu, pro který budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="cacbf-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="cacbf-107">mimo Základní adresa, na které je modul načten.</span><span class="sxs-lookup"><span data-stu-id="cacbf-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cacbf-108">pro Délka `szName` návratové vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="cacbf-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cacbf-109">mimo Ukazatel na celkovou délku znaku v názvu souboru modulu, který je vrácen.</span><span class="sxs-lookup"><span data-stu-id="cacbf-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="cacbf-110">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="cacbf-111">Když se metoda vrátí, tato vyrovnávací paměť obsahuje název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="cacbf-112">mimo Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cacbf-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cacbf-113">Remarks</span></span>  
 <span data-ttu-id="cacbf-114">Pro dynamické moduly je parametr `szName` prázdným řetězcem a základní adresa je 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="cacbf-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="cacbf-115">I když může být metoda `GetModuleInfo` volána, jakmile existuje ID modulu, ID nadřazeného sestavení nebude k dispozici, dokud Profiler neobdrží zpětné volání [ICorProfilerCallback:: ModuleAttachedToAssembly –](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cacbf-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="cacbf-116">Když `GetModuleInfo` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="cacbf-117">To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="cacbf-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="cacbf-118">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="cacbf-119">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetModuleInfo` s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cacbf-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="cacbf-120">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="cacbf-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cacbf-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cacbf-121">Requirements</span></span>  
 <span data-ttu-id="cacbf-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cacbf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cacbf-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cacbf-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cacbf-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cacbf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cacbf-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cacbf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacbf-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cacbf-126">See also</span></span>

- [<span data-ttu-id="cacbf-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cacbf-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cacbf-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="cacbf-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cacbf-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="cacbf-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="cacbf-130">GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="cacbf-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
