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
ms.openlocfilehash: 751f2ac44e543fed76c7031791bb57d75ed0fd48
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498099"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="27238-102">ICorProfilerInfo::GetModuleInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="27238-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="27238-103">Po předaném ID modulu vrátí název souboru modulu a ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="27238-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27238-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="27238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27238-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="27238-106">pro ID modulu, pro který budou načteny informace.</span><span class="sxs-lookup"><span data-stu-id="27238-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="27238-107">mimo Základní adresa, na které je modul načten.</span><span class="sxs-lookup"><span data-stu-id="27238-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="27238-108">pro Délka `szName` návratové vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="27238-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="27238-109">mimo Ukazatel na celkovou délku znaku v názvu souboru modulu, který je vrácen.</span><span class="sxs-lookup"><span data-stu-id="27238-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="27238-110">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="27238-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="27238-111">Když se metoda vrátí, tato vyrovnávací paměť obsahuje název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="27238-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="27238-112">mimo Ukazatel na ID nadřazeného sestavení modulu.</span><span class="sxs-lookup"><span data-stu-id="27238-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27238-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27238-113">Remarks</span></span>  
 <span data-ttu-id="27238-114">Pro dynamické moduly `szName` je parametr prázdný řetězec a základní adresa je 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="27238-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="27238-115">I když `GetModuleInfo` může být metoda volána, jakmile existuje ID modulu, ID nadřazeného sestavení nebude k dispozici, dokud Profiler neobdrží zpětné volání [ICorProfilerCallback:: ModuleAttachedToAssembly –](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27238-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="27238-116">Po `GetModuleInfo` návratu je nutné ověřit, zda `szName` byla vyrovnávací paměť dostatečně velká, aby obsahovala úplný název souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="27238-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="27238-117">Provedete to tak, že porovnáte hodnotu, `pcchName` na kterou odkazuje, s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="27238-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="27238-118">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName` , přidělte větší `szName` vyrovnávací paměť, aktualizujte `cchName` novou, větší velikost a zavolejte `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="27238-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="27238-119">Případně můžete `GetModuleInfo` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="27238-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="27238-120">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetModuleInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="27238-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27238-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27238-121">Requirements</span></span>  
 <span data-ttu-id="27238-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27238-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27238-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="27238-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27238-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="27238-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27238-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27238-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27238-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27238-126">See also</span></span>

- [<span data-ttu-id="27238-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27238-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="27238-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="27238-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="27238-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="27238-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="27238-130">GetModuleInfo2 – metoda</span><span class="sxs-lookup"><span data-stu-id="27238-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
