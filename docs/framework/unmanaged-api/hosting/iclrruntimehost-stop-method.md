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
ms.openlocfilehash: 97a0e6cbbd8972f58f9eedcfeb8aff1f93694064
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765667"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="c7971-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="c7971-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="c7971-103">Zastaví provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c7971-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c7971-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zničit vlákna.</span><span class="sxs-lookup"><span data-stu-id="c7971-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="c7971-105">Musí být ukončen proces k uvolnění těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="c7971-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7971-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7971-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c7971-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7971-107">Return Value</span></span>  
  
|<span data-ttu-id="c7971-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7971-108">HRESULT</span></span>|<span data-ttu-id="c7971-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c7971-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7971-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7971-110">S_OK</span></span>|<span data-ttu-id="c7971-111">`Stop` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c7971-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="c7971-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7971-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7971-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c7971-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7971-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7971-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7971-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c7971-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7971-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7971-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7971-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c7971-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7971-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7971-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7971-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c7971-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7971-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7971-120">E_FAIL</span></span>|<span data-ttu-id="c7971-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c7971-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7971-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c7971-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7971-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c7971-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7971-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7971-124">Requirements</span></span>  
 <span data-ttu-id="c7971-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7971-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7971-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7971-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7971-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7971-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7971-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7971-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7971-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7971-129">See also</span></span>

- [<span data-ttu-id="c7971-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7971-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
