---
title: "IHostAssemblyManager::GetAssemblyStore – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d838ee8383a4e11f5d43c4a3751c4a90503906fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="d5aaf-102">IHostAssemblyManager::GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="d5aaf-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="d5aaf-103">Získá ukazatele rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení načíst pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5aaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5aaf-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5aaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5aaf-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="d5aaf-106">[out] Ukazatel na `IHostAssemblyStore` instanci, nebo hodnotu null, pokud hostitel neimplementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5aaf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5aaf-107">Return Value</span></span>  
  
|<span data-ttu-id="d5aaf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5aaf-108">HRESULT</span></span>|<span data-ttu-id="d5aaf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d5aaf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5aaf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5aaf-110">S_OK</span></span>|<span data-ttu-id="d5aaf-111">`GetAssemblyStore`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="d5aaf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5aaf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5aaf-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5aaf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5aaf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5aaf-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-115">The call timed out.</span></span>|  
|<span data-ttu-id="d5aaf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5aaf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5aaf-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5aaf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5aaf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5aaf-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5aaf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5aaf-120">E_FAIL</span></span>|<span data-ttu-id="d5aaf-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5aaf-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5aaf-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d5aaf-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d5aaf-124">E_NOINTERFACE</span></span>|<span data-ttu-id="d5aaf-125">Hostitel neposkytuje implementace `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5aaf-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5aaf-126">Remarks</span></span>  
 <span data-ttu-id="d5aaf-127">`IHostAssemblyStore`poskytuje metody, které umožňují pro hostitele a vytvořit vazbu k sestavení a moduly nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="d5aaf-128">Hostitelé obvykle poskytují sestavení úložiště umožňující sestavení načíst z formátu než systému souborů.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5aaf-129">Pokud hostitel neimplementuje `IHostAssemblyStore`, `GetAssemblyStore` by měla vrátit má hodnotu HRESULT E_NOINTERFACE a měli nastavit `ppAssemblyStore` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d5aaf-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5aaf-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5aaf-130">Requirements</span></span>  
 <span data-ttu-id="d5aaf-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5aaf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5aaf-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5aaf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5aaf-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5aaf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5aaf-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5aaf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5aaf-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5aaf-135">See Also</span></span>  
 [<span data-ttu-id="d5aaf-136">Ihostassemblymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5aaf-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="d5aaf-137">Ihostassemblystore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5aaf-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
