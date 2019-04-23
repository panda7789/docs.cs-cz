---
title: ICLRRuntimeHost::Start – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608612f6a0f4395092e33ce75fdbd249f19ae4f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172611"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="c4a32-102">ICLRRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="c4a32-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="c4a32-103">Inicializuje modul CLR (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="c4a32-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a32-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c4a32-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4a32-105">Return Value</span></span>  
  
|<span data-ttu-id="c4a32-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4a32-106">HRESULT</span></span>|<span data-ttu-id="c4a32-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a32-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4a32-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4a32-108">S_OK</span></span>|<span data-ttu-id="c4a32-109">`Start` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c4a32-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="c4a32-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4a32-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4a32-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c4a32-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4a32-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4a32-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4a32-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c4a32-113">The call timed out.</span></span>|  
|<span data-ttu-id="c4a32-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4a32-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4a32-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c4a32-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4a32-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4a32-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4a32-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c4a32-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4a32-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4a32-118">E_FAIL</span></span>|<span data-ttu-id="c4a32-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c4a32-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4a32-120">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c4a32-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4a32-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4a32-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4a32-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4a32-122">Remarks</span></span>  
 <span data-ttu-id="c4a32-123">V mnoha scénářích není nutné volat `Start`, protože modul runtime bude inicializovat automaticky na první žádost se spouštět spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c4a32-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="c4a32-124">Můžete však použít `Start` k určení přesně když modul runtime by se měl inicializovat.</span><span class="sxs-lookup"><span data-stu-id="c4a32-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a32-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4a32-125">Requirements</span></span>  
 <span data-ttu-id="c4a32-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4a32-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a32-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4a32-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4a32-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4a32-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a32-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a32-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a32-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4a32-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="c4a32-131">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4a32-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
