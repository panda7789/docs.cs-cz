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
ms.openlocfilehash: 85116244ad21842fab025ddd48106deef75f210b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166969"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="110b8-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="110b8-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="110b8-103">Zastaví provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="110b8-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="110b8-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zničit vlákna.</span><span class="sxs-lookup"><span data-stu-id="110b8-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="110b8-105">Musí být ukončen proces k uvolnění těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="110b8-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110b8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="110b8-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="110b8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="110b8-107">Return Value</span></span>  
  
|<span data-ttu-id="110b8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="110b8-108">HRESULT</span></span>|<span data-ttu-id="110b8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="110b8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="110b8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="110b8-110">S_OK</span></span>|`Stop` <span data-ttu-id="110b8-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="110b8-111">returned successfully.</span></span>|  
|<span data-ttu-id="110b8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="110b8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="110b8-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="110b8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="110b8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="110b8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="110b8-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="110b8-115">The call timed out.</span></span>|  
|<span data-ttu-id="110b8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="110b8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="110b8-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="110b8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="110b8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="110b8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="110b8-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="110b8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="110b8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="110b8-120">E_FAIL</span></span>|<span data-ttu-id="110b8-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="110b8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="110b8-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="110b8-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="110b8-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="110b8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="110b8-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="110b8-124">Requirements</span></span>  
 <span data-ttu-id="110b8-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110b8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110b8-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="110b8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="110b8-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="110b8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="110b8-128">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="110b8-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="110b8-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="110b8-129">See also</span></span>

- [<span data-ttu-id="110b8-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="110b8-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
