---
title: "ICLRRuntimeHost::Stop – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="ca33a-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="ca33a-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="ca33a-103">Ukončí provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ca33a-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca33a-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zrušení vláken.</span><span class="sxs-lookup"><span data-stu-id="ca33a-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="ca33a-105">Proces k uvolnění těchto prostředků musí být ukončen.</span><span class="sxs-lookup"><span data-stu-id="ca33a-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca33a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca33a-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ca33a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ca33a-107">Return Value</span></span>  
  
|<span data-ttu-id="ca33a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca33a-108">HRESULT</span></span>|<span data-ttu-id="ca33a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ca33a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca33a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca33a-110">S_OK</span></span>|<span data-ttu-id="ca33a-111">`Stop`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ca33a-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="ca33a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca33a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca33a-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ca33a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca33a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca33a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca33a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ca33a-115">The call timed out.</span></span>|  
|<span data-ttu-id="ca33a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca33a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca33a-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ca33a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca33a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca33a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca33a-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ca33a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca33a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca33a-120">E_FAIL</span></span>|<span data-ttu-id="ca33a-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ca33a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca33a-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ca33a-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca33a-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca33a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca33a-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca33a-124">Requirements</span></span>  
 <span data-ttu-id="ca33a-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca33a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca33a-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca33a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca33a-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca33a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca33a-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca33a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca33a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca33a-129">See Also</span></span>  
 [<span data-ttu-id="ca33a-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca33a-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
