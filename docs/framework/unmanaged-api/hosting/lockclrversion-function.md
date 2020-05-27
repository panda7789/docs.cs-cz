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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008492"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="40e28-102">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="40e28-102">LockClrVersion Function</span></span>
<span data-ttu-id="40e28-103">Umožňuje hostiteli určit, která verze modulu CLR (Common Language Runtime) bude použita v rámci procesu před explicitní inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="40e28-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="40e28-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="40e28-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40e28-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40e28-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40e28-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="40e28-107">pro Funkce, která má být volána modulem CLR při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="40e28-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="40e28-108">pro Funkce, která má být volána hostitelem pro informování modulu CLR, který spouští inicializaci.</span><span class="sxs-lookup"><span data-stu-id="40e28-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="40e28-109">pro Funkce, která má být volána hostitelem pro informování CLR o dokončení inicializace.</span><span class="sxs-lookup"><span data-stu-id="40e28-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40e28-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40e28-110">Return Value</span></span>  
 <span data-ttu-id="40e28-111">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="40e28-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="40e28-112">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="40e28-112">Return code</span></span>|<span data-ttu-id="40e28-113">Description</span><span class="sxs-lookup"><span data-stu-id="40e28-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="40e28-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="40e28-114">S_OK</span></span>|<span data-ttu-id="40e28-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="40e28-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="40e28-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="40e28-116">E_INVALIDARG</span></span>|<span data-ttu-id="40e28-117">Jeden nebo více argumentů má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="40e28-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e28-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40e28-118">Remarks</span></span>  
 <span data-ttu-id="40e28-119">Hostitel volá `LockClrVersion` před inicializací modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="40e28-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="40e28-120">`LockClrVersion`přijímá tři parametry, z nichž všechny jsou zpětná volání typu [FLockClrVersionCallback –](flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="40e28-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="40e28-121">Tento typ je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="40e28-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="40e28-122">Při inicializaci modulu runtime dojde k následujícím krokům:</span><span class="sxs-lookup"><span data-stu-id="40e28-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="40e28-123">Hostitel volá [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) nebo jednu z dalších funkcí inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="40e28-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="40e28-124">Alternativně může hostitel inicializovat modul runtime pomocí aktivace objektu COM.</span><span class="sxs-lookup"><span data-stu-id="40e28-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="40e28-125">Modul runtime zavolá funkci určenou `hostCallback` parametrem.</span><span class="sxs-lookup"><span data-stu-id="40e28-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="40e28-126">Funkce zadaná v `hostCallback` pak provede následující posloupnost volání:</span><span class="sxs-lookup"><span data-stu-id="40e28-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="40e28-127">Funkce určená `pBeginHostSetup` parametrem.</span><span class="sxs-lookup"><span data-stu-id="40e28-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="40e28-128">`CorBindToRuntimeEx`(nebo jiná funkce inicializace modulu runtime).</span><span class="sxs-lookup"><span data-stu-id="40e28-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="40e28-129">[ICLRRuntimeHost:: SetHostControl –](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="40e28-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="40e28-130">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="40e28-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="40e28-131">Funkce určená `pEndHostSetup` parametrem.</span><span class="sxs-lookup"><span data-stu-id="40e28-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="40e28-132">Všechna volání od `pBeginHostSetup` do `pEndHostSetup` musí být provedena v jednom vlákně nebo vlákně se stejným logickým zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="40e28-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="40e28-133">Toto vlákno se může lišit od vlákna, na kterém `hostCallback` je volána.</span><span class="sxs-lookup"><span data-stu-id="40e28-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e28-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40e28-134">Requirements</span></span>  
 <span data-ttu-id="40e28-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e28-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e28-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40e28-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40e28-137">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40e28-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40e28-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e28-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e28-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="40e28-139">See also</span></span>

- [<span data-ttu-id="40e28-140">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="40e28-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
