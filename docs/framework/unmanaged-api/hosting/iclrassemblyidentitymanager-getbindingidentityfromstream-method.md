---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dc4e3adf5adec1aa4626a31b6a9391e2a04f1ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970089"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="5fe4f-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="5fe4f-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="5fe4f-103">Získá data identit canonical sestavení pro sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fe4f-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fe4f-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="5fe4f-106">[in] Sestavení datový proud, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5fe4f-107">[in] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="5fe4f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje aktuální verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5fe4f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="5fe4f-109">[out] Vyrovnávací paměť obsahující data identit neprůhledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="5fe4f-110">[out v] Velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fe4f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5fe4f-111">Return Value</span></span>  
  
|<span data-ttu-id="5fe4f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fe4f-112">HRESULT</span></span>|<span data-ttu-id="5fe4f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5fe4f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fe4f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fe4f-114">S_OK</span></span>|<span data-ttu-id="5fe4f-115">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="5fe4f-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5fe4f-116">E_INVALIDARG</span></span>|<span data-ttu-id="5fe4f-117">Zadané `pStream` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="5fe4f-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5fe4f-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5fe4f-119">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="5fe4f-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5fe4f-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5fe4f-121">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5fe4f-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5fe4f-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5fe4f-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-123">The call timed out.</span></span>|  
|<span data-ttu-id="5fe4f-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5fe4f-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5fe4f-125">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5fe4f-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5fe4f-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5fe4f-127">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5fe4f-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5fe4f-128">E_FAIL</span></span>|<span data-ttu-id="5fe4f-129">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5fe4f-130">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5fe4f-131">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5fe4f-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fe4f-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fe4f-132">Requirements</span></span>  
 <span data-ttu-id="5fe4f-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe4f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe4f-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5fe4f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5fe4f-135">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5fe4f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fe4f-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe4f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe4f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fe4f-137">See also</span></span>

- [<span data-ttu-id="5fe4f-138">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fe4f-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5fe4f-139">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5fe4f-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
