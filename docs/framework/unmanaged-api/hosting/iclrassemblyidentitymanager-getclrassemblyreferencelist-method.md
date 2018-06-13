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
ms.openlocfilehash: 49962e632ced9aac376791ead672e6910117ee10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434736"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="64df0-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="64df0-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="64df0-103">Získá ukazatele rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instanci ze seznamu zadaný částečného sestavení identit.</span><span class="sxs-lookup"><span data-stu-id="64df0-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64df0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64df0-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64df0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64df0-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="64df0-106">[v] Pole řetězce ukončené hodnotou null ve tvaru "vlastnost name = value...", zadejte seznam identit částečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="64df0-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="64df0-107">[v] Počet položek v `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="64df0-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="64df0-108">[out] Ukazatele rozhraní k `ICLRAssemblyReferenceList` objekt, který obsahuje data identit sestavení pro seznam sestavení zadaný v `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="64df0-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64df0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="64df0-109">Return Value</span></span>  
  
|<span data-ttu-id="64df0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64df0-110">HRESULT</span></span>|<span data-ttu-id="64df0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="64df0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64df0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="64df0-112">S_OK</span></span>|<span data-ttu-id="64df0-113">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="64df0-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="64df0-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64df0-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64df0-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="64df0-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64df0-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64df0-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64df0-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="64df0-117">The call timed out.</span></span>|  
|<span data-ttu-id="64df0-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64df0-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64df0-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="64df0-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64df0-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64df0-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64df0-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="64df0-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64df0-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64df0-122">E_FAIL</span></span>|<span data-ttu-id="64df0-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="64df0-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64df0-124">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="64df0-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64df0-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="64df0-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64df0-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64df0-126">Requirements</span></span>  
 <span data-ttu-id="64df0-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64df0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64df0-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64df0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64df0-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64df0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64df0-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64df0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64df0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="64df0-131">See Also</span></span>  
 [<span data-ttu-id="64df0-132">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64df0-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="64df0-133">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64df0-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
