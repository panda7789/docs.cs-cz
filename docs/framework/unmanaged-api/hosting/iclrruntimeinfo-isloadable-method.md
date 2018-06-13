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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432957"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="03a55-102">ICLRRuntimeInfo::IsLoadable – metoda</span><span class="sxs-lookup"><span data-stu-id="03a55-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="03a55-103">Určuje, zda modul runtime přidružené toto rozhraní je možné načíst do aktuální proces, vezme v úvahu další moduly runtime, který může být již načtena do procesu.</span><span class="sxs-lookup"><span data-stu-id="03a55-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a55-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03a55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03a55-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="03a55-106">[out] `true` Pokud tento modul runtime by mohla být načtena do aktuální proces, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="03a55-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03a55-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03a55-107">Return Value</span></span>  
 <span data-ttu-id="03a55-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="03a55-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="03a55-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03a55-109">HRESULT</span></span>|<span data-ttu-id="03a55-110">Popis</span><span class="sxs-lookup"><span data-stu-id="03a55-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03a55-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="03a55-111">S_OK</span></span>|<span data-ttu-id="03a55-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="03a55-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="03a55-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="03a55-113">E_POINTER</span></span>|<span data-ttu-id="03a55-114">`pbLoadable` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="03a55-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a55-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03a55-115">Remarks</span></span>  
 <span data-ttu-id="03a55-116">Pokud jiný modul runtime je již načtena do procesu a v procesu spuštění vedle sebe, mohou být načteny runtime spojené s tímto rozhraním `pbLoadable` vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="03a55-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="03a55-117">Pokud dva moduly Runtime nelze spustit vedle sebe v rámci procesu, `pbLoadable` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="03a55-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="03a55-118">Modul CLR (CLR) verze 4 můžete například spustit-souběžného v rámci jednoho procesu s CLR verze 2.0 nebo CLR verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="03a55-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="03a55-119">Modul CLR verze 1.1 a verze modulu CLR 2.0 však nelze spustit vedle sebe v procesu.</span><span class="sxs-lookup"><span data-stu-id="03a55-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="03a55-120">Pokud jsou načteny žádné moduly runtime do procesu, tato metoda vždy vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="03a55-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a55-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03a55-121">Requirements</span></span>  
 <span data-ttu-id="03a55-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a55-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a55-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03a55-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03a55-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03a55-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03a55-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a55-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a55-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a55-126">See Also</span></span>  
 [<span data-ttu-id="03a55-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03a55-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="03a55-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="03a55-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="03a55-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="03a55-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
