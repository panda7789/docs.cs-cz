---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72bfb896ccff23938a4fc218fb1f95eebcf5bb93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773505"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="3fb38-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="3fb38-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="3fb38-103">Získá ukazatel rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance ze zadaného seznamu identit částečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3fb38-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fb38-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fb38-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="3fb38-106">[in] Řetězec zakončený null ve formě pole "název, vlastnost = hodnota..." které určují seznam identit částečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3fb38-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="3fb38-107">[in] Počet položek v `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="3fb38-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="3fb38-108">[out] Ukazatel rozhraní k `ICLRAssemblyReferenceList` objekt, který obsahuje data identity sestavení pro seznam sestavení zadaná v `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="3fb38-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fb38-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3fb38-109">Return Value</span></span>  
  
|<span data-ttu-id="3fb38-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fb38-110">HRESULT</span></span>|<span data-ttu-id="3fb38-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3fb38-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fb38-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fb38-112">S_OK</span></span>|<span data-ttu-id="3fb38-113">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="3fb38-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="3fb38-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fb38-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fb38-115">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3fb38-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fb38-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fb38-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fb38-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3fb38-117">The call timed out.</span></span>|  
|<span data-ttu-id="3fb38-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fb38-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fb38-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="3fb38-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fb38-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fb38-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fb38-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="3fb38-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fb38-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fb38-122">E_FAIL</span></span>|<span data-ttu-id="3fb38-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="3fb38-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fb38-124">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3fb38-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fb38-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3fb38-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3fb38-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fb38-126">Requirements</span></span>  
 <span data-ttu-id="3fb38-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb38-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb38-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3fb38-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fb38-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fb38-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fb38-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb38-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb38-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fb38-131">See also</span></span>

- [<span data-ttu-id="3fb38-132">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fb38-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3fb38-133">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fb38-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
