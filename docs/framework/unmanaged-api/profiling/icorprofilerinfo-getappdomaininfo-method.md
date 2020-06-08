---
title: ICorProfilerInfo::GetAppDomainInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503026"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="5252e-102">ICorProfilerInfo::GetAppDomainInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="5252e-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="5252e-103">Přijímá ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5252e-103">Accepts an application domain ID.</span></span> <span data-ttu-id="5252e-104">Vrátí název domény aplikace a ID procesu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="5252e-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5252e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5252e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5252e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5252e-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="5252e-107">pro ID domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5252e-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5252e-108">pro Délka `szName` návratové vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="5252e-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5252e-109">mimo Ukazatel na celkovou délku znaku názvu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5252e-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="5252e-110">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5252e-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="5252e-111">Když se metoda vrátí, `szName` bude obsahovat úplný nebo částečný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5252e-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="5252e-112">mimo Ukazatel na ID procesu, který obsahuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5252e-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5252e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5252e-113">Remarks</span></span>  
 <span data-ttu-id="5252e-114">Po návratu této metody je nutné ověřit, zda `szName` byla vyrovnávací paměť dostatečně velká, aby obsahovala úplný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="5252e-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="5252e-115">Provedete to tak, že porovnáte hodnotu, `pcchName` na kterou odkazuje, s hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="5252e-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="5252e-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName` , přidělte větší `szName` vyrovnávací paměť, aktualizujte `cchName` novou, větší velikost a zavolejte `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="5252e-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="5252e-117">Případně můžete `GetAppDomainInfo` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5252e-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5252e-118">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="5252e-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5252e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5252e-119">Requirements</span></span>  
 <span data-ttu-id="5252e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5252e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5252e-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5252e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5252e-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5252e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5252e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5252e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5252e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5252e-124">See also</span></span>

- [<span data-ttu-id="5252e-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5252e-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5252e-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5252e-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5252e-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="5252e-127">Profiling</span></span>](index.md)
