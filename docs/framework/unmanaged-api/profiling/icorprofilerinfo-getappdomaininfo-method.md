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
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864086"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="7b04f-102">ICorProfilerInfo::GetAppDomainInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="7b04f-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="7b04f-103">Přijímá ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b04f-103">Accepts an application domain ID.</span></span> <span data-ttu-id="7b04f-104">Vrátí název domény aplikace a ID procesu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="7b04f-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b04f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b04f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b04f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b04f-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="7b04f-107">pro ID domény aplikace</span><span class="sxs-lookup"><span data-stu-id="7b04f-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7b04f-108">pro Délka `szName` návratové vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="7b04f-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7b04f-109">mimo Ukazatel na celkovou délku znaku názvu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b04f-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="7b04f-110">mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu.</span><span class="sxs-lookup"><span data-stu-id="7b04f-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="7b04f-111">Když se metoda vrátí, `szName` bude obsahovat úplný nebo částečný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b04f-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="7b04f-112">mimo Ukazatel na ID procesu, který obsahuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b04f-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b04f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b04f-113">Remarks</span></span>  
 <span data-ttu-id="7b04f-114">Po návratu této metody je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b04f-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="7b04f-115">To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="7b04f-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="7b04f-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="7b04f-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="7b04f-117">Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetAppDomainInfo` s nulovou délkou `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7b04f-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7b04f-118">Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="7b04f-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b04f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b04f-119">Requirements</span></span>  
 <span data-ttu-id="7b04f-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b04f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b04f-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7b04f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b04f-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b04f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b04f-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b04f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b04f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b04f-124">See also</span></span>

- [<span data-ttu-id="7b04f-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b04f-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7b04f-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7b04f-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7b04f-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="7b04f-127">Profiling</span></span>](index.md)
