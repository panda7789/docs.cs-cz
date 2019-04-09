---
title: IHostAssemblyManager::GetAssemblyStore – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35e38949ce945d93216daffd3c0d91dad6c8739b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092770"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="d97e6-102">IHostAssemblyManager::GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="d97e6-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="d97e6-103">Získá ukazatel rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení zavedených od hostitele.</span><span class="sxs-lookup"><span data-stu-id="d97e6-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d97e6-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d97e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d97e6-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="d97e6-106">[out] Ukazatel na funkci na `IHostAssemblyStore` instanci, nebo hodnotu null, pokud hostitel neimplementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d97e6-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d97e6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d97e6-107">Return Value</span></span>  
  
|<span data-ttu-id="d97e6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d97e6-108">HRESULT</span></span>|<span data-ttu-id="d97e6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d97e6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d97e6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d97e6-110">S_OK</span></span>|`GetAssemblyStore` <span data-ttu-id="d97e6-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d97e6-111">returned successfully.</span></span>|  
|<span data-ttu-id="d97e6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d97e6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d97e6-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d97e6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d97e6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d97e6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d97e6-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d97e6-115">The call timed out.</span></span>|  
|<span data-ttu-id="d97e6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d97e6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d97e6-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d97e6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d97e6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d97e6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d97e6-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d97e6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d97e6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d97e6-120">E_FAIL</span></span>|<span data-ttu-id="d97e6-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d97e6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d97e6-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d97e6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d97e6-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d97e6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d97e6-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d97e6-124">E_NOINTERFACE</span></span>|<span data-ttu-id="d97e6-125">Hostitel neposkytuje implementaci `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d97e6-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d97e6-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d97e6-126">Remarks</span></span>  
 `IHostAssemblyStore` <span data-ttu-id="d97e6-127">poskytuje metody, které umožňují hostitele, který k vytvoření vazby na sestavení a modulů nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d97e6-127">provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="d97e6-128">Hostitelé obvykle poskytují úložiště sestavení umožňující sestavení, který se má načíst z formátů než v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="d97e6-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d97e6-129">Pokud hostitel neimplementuje `IHostAssemblyStore`, `GetAssemblyStore` by měl vrátit hodnotu HRESULT E_NOINTERFACE a nastavte `ppAssemblyStore` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d97e6-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d97e6-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d97e6-130">Requirements</span></span>  
 <span data-ttu-id="d97e6-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97e6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97e6-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d97e6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d97e6-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d97e6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d97e6-134">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d97e6-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d97e6-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d97e6-135">See also</span></span>

- [<span data-ttu-id="d97e6-136">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d97e6-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d97e6-137">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d97e6-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
