---
title: ICLRControl::GetCLRManager – metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615849"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="6bab3-102">ICLRControl::GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6bab3-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="6bab3-103">Získá ukazatel rozhraní na instanci kteréhokoli typu správce, který může hostitel použít ke konfiguraci modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6bab3-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bab3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bab3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bab3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bab3-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="6bab3-106">pro `IID`Typ správce, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="6bab3-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="6bab3-107">`IID`Podporovány jsou následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6bab3-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="6bab3-108">IID_ICLRDebugManager: Určuje, zda `ppObject` bude [ICLRDebugManager](iclrdebugmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-109">IID_ICLRErrorReportingManager: Určuje, zda `ppObject` bude [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-110">IID_ICLRGCManager: Určuje, zda `ppObject` bude [ICLRGCManager](iclrgcmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-111">IID_ICLRHostProtectionManager: Určuje, zda `ppObject` bude [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-112">IID_ICLROnEventManager: Určuje, zda `ppObject` bude [ICLROnEventManager](iclroneventmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-113">IID_ICLRPolicyManager: Určuje, zda `ppObject` bude [ICLRPolicyManager](iclrpolicymanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="6bab3-114">IID_ICLRTaskManager: Určuje, zda `ppObject` bude [ICLRTaskManager](iclrtaskmanager-interface.md)typu.</span><span class="sxs-lookup"><span data-stu-id="6bab3-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="6bab3-115">mimo Ukazatel rozhraní na požadovaného správce nebo hodnotu null, pokud byl požadován neplatný typ správce.</span><span class="sxs-lookup"><span data-stu-id="6bab3-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bab3-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bab3-116">Return Value</span></span>  
  
|<span data-ttu-id="6bab3-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bab3-117">HRESULT</span></span>|<span data-ttu-id="6bab3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6bab3-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6bab3-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bab3-119">S_OK</span></span>|<span data-ttu-id="6bab3-120">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6bab3-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="6bab3-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6bab3-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6bab3-122">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6bab3-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6bab3-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6bab3-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6bab3-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6bab3-124">The call timed out.</span></span>|  
|<span data-ttu-id="6bab3-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6bab3-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6bab3-126">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6bab3-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6bab3-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6bab3-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6bab3-128">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6bab3-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6bab3-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6bab3-129">E_FAIL</span></span>|<span data-ttu-id="6bab3-130">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6bab3-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6bab3-131">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="6bab3-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6bab3-132">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6bab3-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6bab3-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="6bab3-133">E_NOINTERFACE</span></span>|<span data-ttu-id="6bab3-134">Typ rozhraní není podporován.</span><span class="sxs-lookup"><span data-stu-id="6bab3-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bab3-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bab3-135">Requirements</span></span>  
 <span data-ttu-id="6bab3-136">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bab3-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bab3-137">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6bab3-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bab3-138">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bab3-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bab3-139">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bab3-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bab3-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bab3-140">See also</span></span>

- [<span data-ttu-id="6bab3-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bab3-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6bab3-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bab3-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
