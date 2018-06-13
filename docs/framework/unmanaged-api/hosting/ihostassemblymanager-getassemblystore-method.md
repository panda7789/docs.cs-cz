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
ms.openlocfilehash: efad3c6e566ab35a8ba4fbbacf09931e844ce8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438348"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="734e3-102">IHostAssemblyManager::GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="734e3-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="734e3-103">Získá ukazatele rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení načíst pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="734e3-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="734e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="734e3-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="734e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="734e3-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="734e3-106">[out] Ukazatel na `IHostAssemblyStore` instanci, nebo hodnotu null, pokud hostitel neimplementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="734e3-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="734e3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="734e3-107">Return Value</span></span>  
  
|<span data-ttu-id="734e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="734e3-108">HRESULT</span></span>|<span data-ttu-id="734e3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="734e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="734e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="734e3-110">S_OK</span></span>|<span data-ttu-id="734e3-111">`GetAssemblyStore` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="734e3-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="734e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="734e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="734e3-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="734e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="734e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="734e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="734e3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="734e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="734e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="734e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="734e3-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="734e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="734e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="734e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="734e3-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="734e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="734e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="734e3-120">E_FAIL</span></span>|<span data-ttu-id="734e3-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="734e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="734e3-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="734e3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="734e3-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="734e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="734e3-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="734e3-124">E_NOINTERFACE</span></span>|<span data-ttu-id="734e3-125">Hostitel neposkytuje implementace `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="734e3-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="734e3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="734e3-126">Remarks</span></span>  
 <span data-ttu-id="734e3-127">`IHostAssemblyStore` poskytuje metody, které umožňují pro hostitele a vytvořit vazbu k sestavení a moduly nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="734e3-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="734e3-128">Hostitelé obvykle poskytují sestavení úložiště umožňující sestavení načíst z formátu než systému souborů.</span><span class="sxs-lookup"><span data-stu-id="734e3-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="734e3-129">Pokud hostitel neimplementuje `IHostAssemblyStore`, `GetAssemblyStore` by měla vrátit má hodnotu HRESULT E_NOINTERFACE a měli nastavit `ppAssemblyStore` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="734e3-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734e3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="734e3-130">Requirements</span></span>  
 <span data-ttu-id="734e3-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="734e3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="734e3-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="734e3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="734e3-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="734e3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="734e3-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="734e3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734e3-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="734e3-135">See Also</span></span>  
 [<span data-ttu-id="734e3-136">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="734e3-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="734e3-137">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="734e3-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
