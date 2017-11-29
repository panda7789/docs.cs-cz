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
ms.openlocfilehash: 26e1289aa22cda2ab744f1a2715259abbcafc59b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="25f8b-102">ICLRRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="25f8b-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="25f8b-103">Inicializuje modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="25f8b-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f8b-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="25f8b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25f8b-105">Return Value</span></span>  
  
|<span data-ttu-id="25f8b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25f8b-106">HRESULT</span></span>|<span data-ttu-id="25f8b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="25f8b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25f8b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="25f8b-108">S_OK</span></span>|<span data-ttu-id="25f8b-109">`Start`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="25f8b-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="25f8b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25f8b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25f8b-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="25f8b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25f8b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25f8b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25f8b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="25f8b-113">The call timed out.</span></span>|  
|<span data-ttu-id="25f8b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25f8b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25f8b-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="25f8b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25f8b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25f8b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25f8b-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="25f8b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25f8b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25f8b-118">E_FAIL</span></span>|<span data-ttu-id="25f8b-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="25f8b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25f8b-120">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="25f8b-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25f8b-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25f8b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f8b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25f8b-122">Remarks</span></span>  
 <span data-ttu-id="25f8b-123">V mnoha scénářích není nutné volat `Start`, protože modul runtime inicializuje sám automaticky při první požadavek na spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="25f8b-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="25f8b-124">Můžete však použít `Start` zadat přesně v Pokud je třeba inicializovat modul runtime.</span><span class="sxs-lookup"><span data-stu-id="25f8b-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f8b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25f8b-125">Requirements</span></span>  
 <span data-ttu-id="25f8b-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f8b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f8b-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25f8b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25f8b-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25f8b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25f8b-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f8b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f8b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="25f8b-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="25f8b-131">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25f8b-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
