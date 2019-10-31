---
title: ICLRRuntimeInfo::IsLoadable – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 9339bb974c261e62502c760dfaf45651573cbe1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136378"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="91ab5-102">ICLRRuntimeInfo::IsLoadable – metoda</span><span class="sxs-lookup"><span data-stu-id="91ab5-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="91ab5-103">Určuje, zda lze modul runtime spojený s tímto rozhraním načíst do aktuálního procesu, přičemž vezme v úvahu jiné moduly runtime, které mohou být do procesu již načteny.</span><span class="sxs-lookup"><span data-stu-id="91ab5-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ab5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91ab5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ab5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91ab5-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="91ab5-106">[out] `true`, jestli se tento modul runtime mohl načíst do aktuálního procesu. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="91ab5-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91ab5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="91ab5-107">Return Value</span></span>  
 <span data-ttu-id="91ab5-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="91ab5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="91ab5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91ab5-109">HRESULT</span></span>|<span data-ttu-id="91ab5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="91ab5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91ab5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="91ab5-111">S_OK</span></span>|<span data-ttu-id="91ab5-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="91ab5-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="91ab5-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="91ab5-113">E_POINTER</span></span>|<span data-ttu-id="91ab5-114">`pbLoadable` je null.</span><span class="sxs-lookup"><span data-stu-id="91ab5-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91ab5-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91ab5-115">Remarks</span></span>  
 <span data-ttu-id="91ab5-116">Pokud je již do procesu načten jiný modul runtime a modul runtime přidružený k tomuto rozhraní lze načíst pro vnitroprocesové souběžné spouštění, `pbLoadable` vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="91ab5-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="91ab5-117">Pokud tyto dva moduly runtime nemohou běžet souběžně v rámci procesu, `pbLoadable` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="91ab5-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="91ab5-118">Například modul CLR (Common Language Runtime) verze 4 může běžet souběžně v rámci stejného procesu s CLR verze 2,0 nebo CLR verze 1,1.</span><span class="sxs-lookup"><span data-stu-id="91ab5-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="91ab5-119">CLR verze 1,1 a CLR verze 2,0 však nemůže spustit souběžný proces souběžného zpracování.</span><span class="sxs-lookup"><span data-stu-id="91ab5-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="91ab5-120">Pokud nejsou do procesu načteny žádné moduly runtime, tato metoda vždy vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="91ab5-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ab5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91ab5-121">Requirements</span></span>  
 <span data-ttu-id="91ab5-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ab5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ab5-123">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="91ab5-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="91ab5-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91ab5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91ab5-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ab5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ab5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91ab5-126">See also</span></span>

- [<span data-ttu-id="91ab5-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91ab5-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="91ab5-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="91ab5-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="91ab5-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="91ab5-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
