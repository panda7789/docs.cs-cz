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
ms.openlocfilehash: b30f6f5ce22290dc3750cef0171349ec5ff2f76a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126741"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="f1efb-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="f1efb-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="f1efb-103">Získá kanonická data identity sestavení pro sestavení v zadaném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="f1efb-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1efb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1efb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1efb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1efb-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="f1efb-106">pro Stream sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="f1efb-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f1efb-107">pro K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f1efb-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="f1efb-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou aktuální verze modulu CLR (Common Language Runtime) podporuje.</span><span class="sxs-lookup"><span data-stu-id="f1efb-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f1efb-109">mimo Vyrovnávací paměť obsahující data identity neprůhledných sestavení</span><span class="sxs-lookup"><span data-stu-id="f1efb-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f1efb-110">[in, out] Velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f1efb-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1efb-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1efb-111">Return Value</span></span>  
  
|<span data-ttu-id="f1efb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1efb-112">HRESULT</span></span>|<span data-ttu-id="f1efb-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f1efb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1efb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1efb-114">S_OK</span></span>|<span data-ttu-id="f1efb-115">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f1efb-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="f1efb-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f1efb-116">E_INVALIDARG</span></span>|<span data-ttu-id="f1efb-117">Poskytnutý `pStream` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f1efb-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="f1efb-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f1efb-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f1efb-119">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="f1efb-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f1efb-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1efb-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1efb-121">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f1efb-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1efb-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1efb-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1efb-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f1efb-123">The call timed out.</span></span>|  
|<span data-ttu-id="f1efb-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1efb-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1efb-125">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f1efb-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1efb-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1efb-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1efb-127">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f1efb-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1efb-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1efb-128">E_FAIL</span></span>|<span data-ttu-id="f1efb-129">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f1efb-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1efb-130">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f1efb-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1efb-131">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f1efb-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1efb-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1efb-132">Requirements</span></span>  
 <span data-ttu-id="f1efb-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1efb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1efb-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1efb-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1efb-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1efb-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1efb-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1efb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1efb-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1efb-137">See also</span></span>

- [<span data-ttu-id="f1efb-138">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1efb-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f1efb-139">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1efb-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
