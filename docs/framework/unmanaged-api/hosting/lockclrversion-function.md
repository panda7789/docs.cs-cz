---
title: LockClrVersion – funkce
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6742293c1970198ef3d5f5da7d75a0c78e78045c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768405"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="6a26d-102">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="6a26d-102">LockClrVersion Function</span></span>
<span data-ttu-id="6a26d-103">Umožňuje hostiteli zjistit, která verze modulu common language runtime (CLR) se použije v rámci procesu před explicitní inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6a26d-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="6a26d-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6a26d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a26d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a26d-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a26d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a26d-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="6a26d-107">[in] Funkce, které jsou volány při inicializaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6a26d-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="6a26d-108">[in] Spouští se funkce má být volána hostitele tak, aby modul CLR informovat, že inicializace.</span><span class="sxs-lookup"><span data-stu-id="6a26d-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="6a26d-109">[in] Funkce, která se dřív říkalo hostitelem informovat CLR, že inicializace je dokončena.</span><span class="sxs-lookup"><span data-stu-id="6a26d-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a26d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a26d-110">Return Value</span></span>  
 <span data-ttu-id="6a26d-111">Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="6a26d-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="6a26d-112">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="6a26d-112">Return code</span></span>|<span data-ttu-id="6a26d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6a26d-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6a26d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a26d-114">S_OK</span></span>|<span data-ttu-id="6a26d-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6a26d-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="6a26d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6a26d-116">E_INVALIDARG</span></span>|<span data-ttu-id="6a26d-117">Jeden nebo více parametrů má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6a26d-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a26d-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a26d-118">Remarks</span></span>  
 <span data-ttu-id="6a26d-119">Volání hostitele `LockClrVersion` před inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6a26d-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="6a26d-120">`LockClrVersion` přijímá tři parametry, které jsou zpětná volání typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="6a26d-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="6a26d-121">Tento typ je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a26d-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="6a26d-122">Při inicializaci modulu runtime dojde k následujícím krokům:</span><span class="sxs-lookup"><span data-stu-id="6a26d-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="6a26d-123">Volání hostitele [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jeden z jiné funkce inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6a26d-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="6a26d-124">Alternativně může hostitele inicializovat modul runtime pomocí aktivace objektu COM.</span><span class="sxs-lookup"><span data-stu-id="6a26d-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="6a26d-125">Modul runtime volá funkci určené `hostCallback` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a26d-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="6a26d-126">Funkce určené `hostCallback` pak provede následující posloupnost volání:</span><span class="sxs-lookup"><span data-stu-id="6a26d-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="6a26d-127">Určené funkce `pBeginHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a26d-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="6a26d-128">`CorBindToRuntimeEx` (nebo jinou funkci inicializace modulu runtime).</span><span class="sxs-lookup"><span data-stu-id="6a26d-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="6a26d-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a26d-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="6a26d-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a26d-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="6a26d-131">Určené funkce `pEndHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a26d-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="6a26d-132">Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí vyskytovat na jednoho vlákna nebo vlákénka se stejným zásobníkem logické.</span><span class="sxs-lookup"><span data-stu-id="6a26d-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="6a26d-133">Toto vlákno může lišit od vlákna, na kterém `hostCallback` je volána.</span><span class="sxs-lookup"><span data-stu-id="6a26d-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a26d-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a26d-134">Requirements</span></span>  
 <span data-ttu-id="6a26d-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a26d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a26d-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a26d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a26d-137">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a26d-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a26d-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a26d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a26d-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a26d-139">See also</span></span>

- [<span data-ttu-id="6a26d-140">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6a26d-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
