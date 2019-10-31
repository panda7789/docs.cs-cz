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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133775"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="53e6b-102">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="53e6b-102">LockClrVersion Function</span></span>
<span data-ttu-id="53e6b-103">Umožňuje hostiteli určit, která verze modulu CLR (Common Language Runtime) bude použita v rámci procesu před explicitní inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="53e6b-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="53e6b-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="53e6b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e6b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e6b-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e6b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="53e6b-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="53e6b-107">pro Funkce, která má být volána modulem CLR při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="53e6b-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="53e6b-108">pro Funkce, která má být volána hostitelem pro informování modulu CLR, který spouští inicializaci.</span><span class="sxs-lookup"><span data-stu-id="53e6b-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="53e6b-109">pro Funkce, která má být volána hostitelem pro informování CLR o dokončení inicializace.</span><span class="sxs-lookup"><span data-stu-id="53e6b-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53e6b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="53e6b-110">Return Value</span></span>  
 <span data-ttu-id="53e6b-111">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="53e6b-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="53e6b-112">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="53e6b-112">Return code</span></span>|<span data-ttu-id="53e6b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="53e6b-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="53e6b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="53e6b-114">S_OK</span></span>|<span data-ttu-id="53e6b-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="53e6b-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="53e6b-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="53e6b-116">E_INVALIDARG</span></span>|<span data-ttu-id="53e6b-117">Jeden nebo více argumentů má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="53e6b-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e6b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53e6b-118">Remarks</span></span>  
 <span data-ttu-id="53e6b-119">Hostitel volá `LockClrVersion` před inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="53e6b-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="53e6b-120">`LockClrVersion` používá tři parametry, z nichž všechny jsou zpětná volání typu [FLockClrVersionCallback –](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="53e6b-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="53e6b-121">Tento typ je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="53e6b-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="53e6b-122">Při inicializaci modulu runtime dojde k následujícím krokům:</span><span class="sxs-lookup"><span data-stu-id="53e6b-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="53e6b-123">Hostitel volá [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jednu z dalších funkcí inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="53e6b-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="53e6b-124">Alternativně může hostitel inicializovat modul runtime pomocí aktivace objektu COM.</span><span class="sxs-lookup"><span data-stu-id="53e6b-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="53e6b-125">Modul runtime zavolá funkci určenou parametrem `hostCallback`.</span><span class="sxs-lookup"><span data-stu-id="53e6b-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="53e6b-126">Funkce určená `hostCallback` pak provede následující posloupnost volání:</span><span class="sxs-lookup"><span data-stu-id="53e6b-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="53e6b-127">Funkce určená parametrem `pBeginHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="53e6b-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="53e6b-128">`CorBindToRuntimeEx` (nebo jiná funkce inicializace modulu runtime).</span><span class="sxs-lookup"><span data-stu-id="53e6b-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="53e6b-129">[ICLRRuntimeHost:: SetHostControl –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="53e6b-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="53e6b-130">[ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="53e6b-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="53e6b-131">Funkce určená parametrem `pEndHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="53e6b-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="53e6b-132">Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí nastat v jednom vlákně nebo vlákně se stejným logickým zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="53e6b-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="53e6b-133">Toto vlákno se může lišit od vlákna, na kterém je volána `hostCallback`.</span><span class="sxs-lookup"><span data-stu-id="53e6b-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e6b-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53e6b-134">Requirements</span></span>  
 <span data-ttu-id="53e6b-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e6b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e6b-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53e6b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53e6b-137">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53e6b-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53e6b-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e6b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e6b-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53e6b-139">See also</span></span>

- [<span data-ttu-id="53e6b-140">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="53e6b-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
