---
title: ICorProfilerInfo::GetAssemblyInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 41083b2fcd61a9a726e835c3d5710308aa634600
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498606"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="0cea4-102">ICorProfilerInfo::GetAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="0cea4-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="0cea4-103">Přijímá ID sestavení a vrací název sestavení a ID jeho modulu manifestu.</span><span class="sxs-lookup"><span data-stu-id="0cea4-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cea4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cea4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cea4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cea4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="0cea4-106">pro Identifikátor sestavení</span><span class="sxs-lookup"><span data-stu-id="0cea4-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0cea4-107">pro Délka v znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="0cea4-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0cea4-108">mimo Ukazatel na celkovou délku znaku v názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cea4-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0cea4-109">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0cea4-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="0cea4-110">Když funkce vrátí, bude obsahovat název sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cea4-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="0cea4-111">mimo Ukazatel na ID domény aplikace, která obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cea4-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0cea4-112">mimo Ukazatel na ID modulu manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cea4-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cea4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cea4-113">Remarks</span></span>  
 <span data-ttu-id="0cea4-114">Po návratu této metody je nutné ověřit, zda `szName` byla vyrovnávací paměť dostatečně velká, aby obsahovala úplný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cea4-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="0cea4-115">Provedete to tak, že porovnáte hodnotu, `pcchName` na kterou odkazuje, s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="0cea4-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0cea4-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName` , přidělte větší `szName` vyrovnávací paměť, aktualizujte `cchName` novou, větší velikost a zavolejte `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="0cea4-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="0cea4-117">Případně můžete `GetAssemblyInfo` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0cea4-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0cea4-118">Velikost vyrovnávací paměti pak můžete upravit na základě hodnoty vrácené v rámci `pcchName` a zavolat `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="0cea4-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cea4-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cea4-119">Requirements</span></span>  
 <span data-ttu-id="0cea4-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cea4-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cea4-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0cea4-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cea4-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0cea4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cea4-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cea4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cea4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cea4-124">See also</span></span>

- [<span data-ttu-id="0cea4-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cea4-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="0cea4-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0cea4-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0cea4-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="0cea4-127">Profiling</span></span>](index.md)
