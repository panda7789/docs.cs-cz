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
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615979"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="ed342-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="ed342-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="ed342-103">Získá kanonická data identity sestavení pro sestavení v zadaném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="ed342-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed342-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed342-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed342-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="ed342-106">pro Stream sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="ed342-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ed342-107">pro K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ed342-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ed342-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou aktuální verze modulu CLR (Common Language Runtime) podporuje.</span><span class="sxs-lookup"><span data-stu-id="ed342-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ed342-109">mimo Vyrovnávací paměť obsahující data identity neprůhledných sestavení</span><span class="sxs-lookup"><span data-stu-id="ed342-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ed342-110">[in, out] Velikost `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="ed342-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed342-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed342-111">Return Value</span></span>  
  
|<span data-ttu-id="ed342-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed342-112">HRESULT</span></span>|<span data-ttu-id="ed342-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ed342-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed342-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed342-114">S_OK</span></span>|<span data-ttu-id="ed342-115">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ed342-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ed342-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ed342-116">E_INVALIDARG</span></span>|<span data-ttu-id="ed342-117">Zadaná hodnota `pStream` je null.</span><span class="sxs-lookup"><span data-stu-id="ed342-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="ed342-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ed342-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ed342-119">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="ed342-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ed342-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed342-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed342-121">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ed342-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed342-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed342-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed342-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ed342-123">The call timed out.</span></span>|  
|<span data-ttu-id="ed342-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed342-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed342-125">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ed342-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed342-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed342-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed342-127">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ed342-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed342-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed342-128">E_FAIL</span></span>|<span data-ttu-id="ed342-129">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ed342-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed342-130">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ed342-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed342-131">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed342-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed342-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed342-132">Requirements</span></span>  
 <span data-ttu-id="ed342-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed342-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed342-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed342-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed342-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed342-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed342-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed342-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed342-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed342-137">See also</span></span>

- [<span data-ttu-id="ed342-138">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed342-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ed342-139">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed342-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
