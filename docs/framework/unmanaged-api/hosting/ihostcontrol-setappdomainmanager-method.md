---
title: IHostControl::SetAppDomainManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 74ffc5c92402808ae566d7cb014d9d920c384ae8
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804926"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="f43b7-102">IHostControl::SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="f43b7-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="f43b7-103">Upozorňuje hostitele, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="f43b7-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f43b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f43b7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f43b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f43b7-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="f43b7-106">pro Číselný identifikátor vybraného <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f43b7-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="f43b7-107">pro Ukazatel na <xref:System.AppDomainManager> objekt, který Host implementuje `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="f43b7-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f43b7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f43b7-108">Return Value</span></span>  
  
|<span data-ttu-id="f43b7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f43b7-109">HRESULT</span></span>|<span data-ttu-id="f43b7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f43b7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f43b7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f43b7-111">S_OK</span></span>|<span data-ttu-id="f43b7-112">`SetAppDomainManager`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f43b7-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="f43b7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f43b7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f43b7-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f43b7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f43b7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f43b7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f43b7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f43b7-116">The call timed out.</span></span>|  
|<span data-ttu-id="f43b7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f43b7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f43b7-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f43b7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f43b7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f43b7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f43b7-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f43b7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f43b7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f43b7-121">E_FAIL</span></span>|<span data-ttu-id="f43b7-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f43b7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f43b7-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f43b7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f43b7-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f43b7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f43b7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f43b7-125">Remarks</span></span>  
 <span data-ttu-id="f43b7-126"><xref:System.AppDomainManager>Poskytuje hostiteli mechanismus pro zavedení do spravovaného kódu a pro řízení vytváření a nastavení každého z nich <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f43b7-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="f43b7-127"><xref:System.AppDomainManager>Při vytvoření je načten do každého <xref:System.AppDomain> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f43b7-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="f43b7-128">Pokud se zvolí, CLR upozorní hostitele, že byla vytvořena doména aplikace, nastavením hodnoty `pUnkAppDomainManager` parametru.</span><span class="sxs-lookup"><span data-stu-id="f43b7-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="f43b7-129">V rámci implementace `SetAppDomainManager` metody může hostitel nastavit název sestavení a typ pro správce aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="f43b7-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f43b7-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f43b7-130">Requirements</span></span>  
 <span data-ttu-id="f43b7-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f43b7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f43b7-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f43b7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f43b7-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f43b7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f43b7-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f43b7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f43b7-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f43b7-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="f43b7-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f43b7-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
