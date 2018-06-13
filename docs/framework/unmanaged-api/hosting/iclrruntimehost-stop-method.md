---
title: ICLRRuntimeHost::Stop – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d479e271c2cc4ebf9ea6ff349fd28bff37c3857
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436095"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="796f3-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="796f3-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="796f3-103">Ukončí provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="796f3-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="796f3-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zrušení vláken.</span><span class="sxs-lookup"><span data-stu-id="796f3-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="796f3-105">Proces k uvolnění těchto prostředků musí být ukončen.</span><span class="sxs-lookup"><span data-stu-id="796f3-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796f3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="796f3-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="796f3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="796f3-107">Return Value</span></span>  
  
|<span data-ttu-id="796f3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="796f3-108">HRESULT</span></span>|<span data-ttu-id="796f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="796f3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="796f3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="796f3-110">S_OK</span></span>|<span data-ttu-id="796f3-111">`Stop` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="796f3-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="796f3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="796f3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="796f3-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="796f3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="796f3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="796f3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="796f3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="796f3-115">The call timed out.</span></span>|  
|<span data-ttu-id="796f3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="796f3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="796f3-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="796f3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="796f3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="796f3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="796f3-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="796f3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="796f3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="796f3-120">E_FAIL</span></span>|<span data-ttu-id="796f3-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="796f3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="796f3-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="796f3-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="796f3-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="796f3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="796f3-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="796f3-124">Requirements</span></span>  
 <span data-ttu-id="796f3-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="796f3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796f3-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="796f3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="796f3-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="796f3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="796f3-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796f3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796f3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="796f3-129">See Also</span></span>  
 [<span data-ttu-id="796f3-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="796f3-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
