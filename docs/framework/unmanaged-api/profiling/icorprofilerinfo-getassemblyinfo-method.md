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
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864125"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="46143-102">ICorProfilerInfo::GetAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="46143-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="46143-103">Přijímá ID sestavení a vrací název sestavení a ID jeho modulu manifestu.</span><span class="sxs-lookup"><span data-stu-id="46143-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46143-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46143-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="46143-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46143-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="46143-106">pro Identifikátor sestavení</span><span class="sxs-lookup"><span data-stu-id="46143-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="46143-107">pro Délka `szName`znaků.</span><span class="sxs-lookup"><span data-stu-id="46143-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="46143-108">mimo Ukazatel na celkovou délku znaku v názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="46143-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="46143-109">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="46143-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="46143-110">Když funkce vrátí, bude obsahovat název sestavení.</span><span class="sxs-lookup"><span data-stu-id="46143-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="46143-111">mimo Ukazatel na ID domény aplikace, která obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="46143-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="46143-112">mimo Ukazatel na ID modulu manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="46143-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46143-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46143-113">Remarks</span></span>  
 <span data-ttu-id="46143-114">Po návratu této metody je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="46143-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="46143-115">To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="46143-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="46143-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="46143-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="46143-117">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetAssemblyInfo` s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="46143-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="46143-118">Velikost vyrovnávací paměti pak můžete upravit na základě hodnoty vrácené v `pcchName` a volat `GetAssemblyInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="46143-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46143-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46143-119">Requirements</span></span>  
 <span data-ttu-id="46143-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46143-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46143-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="46143-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46143-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="46143-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46143-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46143-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46143-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46143-124">See also</span></span>

- [<span data-ttu-id="46143-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46143-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="46143-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="46143-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="46143-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="46143-127">Profiling</span></span>](index.md)
