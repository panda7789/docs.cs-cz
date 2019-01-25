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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbf52a352000150766cd9a8277278491ad7d5152
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616729"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="aaa8b-102">ICorProfilerInfo::GetAppDomainInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="aaa8b-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="aaa8b-103">Přijímá identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-103">Accepts an application domain ID.</span></span> <span data-ttu-id="aaa8b-104">Vrátí název domény aplikace a ID procesu, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa8b-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aaa8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaa8b-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="aaa8b-107">[in] ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="aaa8b-108">[in] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="aaa8b-109">[out] Ukazatel na celkový počet znaků názvu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="aaa8b-110">[out] Pokud volající širokého znaku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="aaa8b-111">Po návratu metody `szName` bude obsahovat název domény aplikace celé nebo jeho část.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="aaa8b-112">[out] Ukazatel na ID procesu, která obsahuje doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaa8b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaa8b-113">Remarks</span></span>  
 <span data-ttu-id="aaa8b-114">Po návratu tato metoda je nutné ověřit, `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="aaa8b-115">K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="aaa8b-116">Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="aaa8b-117">Alternativně můžete nejprve volat `GetAppDomainInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="aaa8b-118">Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.</span><span class="sxs-lookup"><span data-stu-id="aaa8b-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa8b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaa8b-119">Requirements</span></span>  
 <span data-ttu-id="aaa8b-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa8b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa8b-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aaa8b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aaa8b-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaa8b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaa8b-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa8b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa8b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaa8b-124">See also</span></span>
- [<span data-ttu-id="aaa8b-125">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaa8b-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="aaa8b-126">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="aaa8b-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="aaa8b-127">Profilace</span><span class="sxs-lookup"><span data-stu-id="aaa8b-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
