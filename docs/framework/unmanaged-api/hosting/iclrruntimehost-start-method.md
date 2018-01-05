---
title: "ICLRRuntimeHost::Start – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9705e4449da3b485bef7e7250ca08473d51387b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="13729-102">ICLRRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="13729-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="13729-103">Inicializuje modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="13729-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13729-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13729-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="13729-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13729-105">Return Value</span></span>  
  
|<span data-ttu-id="13729-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13729-106">HRESULT</span></span>|<span data-ttu-id="13729-107">Popis</span><span class="sxs-lookup"><span data-stu-id="13729-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13729-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="13729-108">S_OK</span></span>|<span data-ttu-id="13729-109">`Start`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="13729-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="13729-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13729-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13729-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="13729-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13729-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13729-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13729-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="13729-113">The call timed out.</span></span>|  
|<span data-ttu-id="13729-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13729-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13729-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="13729-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13729-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13729-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13729-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="13729-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13729-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13729-118">E_FAIL</span></span>|<span data-ttu-id="13729-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="13729-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13729-120">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="13729-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13729-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13729-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13729-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13729-122">Remarks</span></span>  
 <span data-ttu-id="13729-123">V mnoha scénářích není nutné volat `Start`, protože modul runtime inicializuje sám automaticky při první požadavek na spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="13729-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="13729-124">Můžete však použít `Start` zadat přesně v Pokud je třeba inicializovat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="13729-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13729-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13729-125">Requirements</span></span>  
 <span data-ttu-id="13729-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13729-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13729-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13729-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13729-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13729-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13729-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13729-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13729-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="13729-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="13729-131">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13729-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
