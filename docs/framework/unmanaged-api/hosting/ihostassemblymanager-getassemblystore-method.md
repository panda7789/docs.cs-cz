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
ms.openlocfilehash: 62965fa928522052b6885769e02c0211ca8d3fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937933"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="3e02f-102">IHostAssemblyManager::GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="3e02f-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="3e02f-103">Získá ukazatel rozhraní na [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , který představuje seznam sestavení načtených hostitelem.</span><span class="sxs-lookup"><span data-stu-id="3e02f-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e02f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e02f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e02f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e02f-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="3e02f-106">mimo Ukazatel na `IHostAssemblyStore` funkci, nebo hodnota null, pokud hostitel neimplementuje `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="3e02f-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e02f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e02f-107">Return Value</span></span>  
  
|<span data-ttu-id="3e02f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e02f-108">HRESULT</span></span>|<span data-ttu-id="3e02f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3e02f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e02f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e02f-110">S_OK</span></span>|<span data-ttu-id="3e02f-111">`GetAssemblyStore`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="3e02f-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="3e02f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e02f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e02f-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3e02f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e02f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e02f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e02f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3e02f-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e02f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e02f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e02f-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3e02f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e02f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e02f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e02f-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3e02f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e02f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e02f-120">E_FAIL</span></span>|<span data-ttu-id="3e02f-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3e02f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e02f-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3e02f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e02f-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e02f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e02f-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="3e02f-124">E_NOINTERFACE</span></span>|<span data-ttu-id="3e02f-125">Hostitel neposkytuje implementaci `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="3e02f-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e02f-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e02f-126">Remarks</span></span>  
 <span data-ttu-id="3e02f-127">`IHostAssemblyStore`poskytuje metody, které umožňují hostiteli vytvořit vazby na sestavení a moduly nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="3e02f-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="3e02f-128">Hostitelé obvykle poskytují úložiště sestavení, aby bylo možné načíst sestavení z jiných formátů než do systému souborů.</span><span class="sxs-lookup"><span data-stu-id="3e02f-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e02f-129">Pokud hostitel neimplementuje `IHostAssemblyStore`, `GetAssemblyStore` měla by vrátit hodnotu HRESULT E_NOINTERFACE a měla by být nastavena `ppAssemblyStore` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3e02f-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e02f-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e02f-130">Requirements</span></span>  
 <span data-ttu-id="3e02f-131">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e02f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e02f-132">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3e02f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e02f-133">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3e02f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e02f-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e02f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e02f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e02f-135">See also</span></span>

- [<span data-ttu-id="3e02f-136">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e02f-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="3e02f-137">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e02f-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
