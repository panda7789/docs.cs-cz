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
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101585"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="2d8d0-102">ICLRRuntimeInfo::IsLoadable – metoda</span><span class="sxs-lookup"><span data-stu-id="2d8d0-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="2d8d0-103">Určuje, zda modul runtime spojený s tímto rozhraním je možné načíst do aktuální proces zohledněním jiné moduly runtime, který může být již načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d8d0-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d8d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d8d0-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="2d8d0-106">[out] `true` Pokud tento modul runtime může být načtena do aktuální proces; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d8d0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d8d0-107">Return Value</span></span>  
 <span data-ttu-id="2d8d0-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d8d0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d8d0-109">HRESULT</span></span>|<span data-ttu-id="2d8d0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2d8d0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d8d0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d8d0-111">S_OK</span></span>|<span data-ttu-id="2d8d0-112">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="2d8d0-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2d8d0-113">E_POINTER</span></span>|<span data-ttu-id="2d8d0-114">`pbLoadable` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d8d0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d8d0-115">Remarks</span></span>  
 <span data-ttu-id="2d8d0-116">Pokud se jiný modul runtime je již načten do procesu a pro provádění vnitroprocesové vedle sebe, je možné načíst modul runtime spojený s tímto rozhraním `pbLoadable` vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="2d8d0-117">Pokud dva moduly runtime nemůže spustit vedle sebe v procesu, `pbLoadable` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="2d8d0-118">Modul CLR verze 4 (CLR) můžete například spustit vedle sebe ve stejném procesu s CLR verze 2.0 nebo CLR verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="2d8d0-119">CLR verze 1.1 a 2.0 verze modulu CLR však nelze spustit vedle sebe v procesu.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="2d8d0-120">Pokud nejsou načteny žádné moduly runtime do procesu, vrátí tato metoda vždy `true`.</span><span class="sxs-lookup"><span data-stu-id="2d8d0-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d8d0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d8d0-121">Requirements</span></span>  
 <span data-ttu-id="2d8d0-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d8d0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d8d0-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d8d0-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d8d0-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d8d0-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d8d0-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d8d0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8d0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d8d0-126">See also</span></span>

- [<span data-ttu-id="2d8d0-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d8d0-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2d8d0-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2d8d0-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2d8d0-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="2d8d0-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
