---
title: "ICLRRuntimeHost::Stop – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3798c4fc451b78257373c0ac47a5e7e7c27dd048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="fbca2-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="fbca2-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="fbca2-103">Ukončí provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fbca2-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fbca2-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zrušení vláken.</span><span class="sxs-lookup"><span data-stu-id="fbca2-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="fbca2-105">Proces k uvolnění těchto prostředků musí být ukončen.</span><span class="sxs-lookup"><span data-stu-id="fbca2-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbca2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbca2-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fbca2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fbca2-107">Return Value</span></span>  
  
|<span data-ttu-id="fbca2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbca2-108">HRESULT</span></span>|<span data-ttu-id="fbca2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fbca2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbca2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbca2-110">S_OK</span></span>|<span data-ttu-id="fbca2-111">`Stop`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fbca2-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="fbca2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbca2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbca2-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fbca2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbca2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbca2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbca2-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fbca2-115">The call timed out.</span></span>|  
|<span data-ttu-id="fbca2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbca2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbca2-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="fbca2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbca2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbca2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbca2-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="fbca2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbca2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbca2-120">E_FAIL</span></span>|<span data-ttu-id="fbca2-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="fbca2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbca2-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fbca2-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbca2-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbca2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbca2-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbca2-124">Requirements</span></span>  
 <span data-ttu-id="fbca2-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbca2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbca2-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbca2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbca2-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbca2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbca2-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbca2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbca2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbca2-129">See Also</span></span>  
 [<span data-ttu-id="fbca2-130">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbca2-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
