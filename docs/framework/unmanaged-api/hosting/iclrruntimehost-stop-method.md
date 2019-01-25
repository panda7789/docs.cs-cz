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
ms.openlocfilehash: 71d4167d17b20c08c2cbc62d2ac0c1cddd88e527
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634430"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="d1179-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="d1179-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="d1179-103">Zastaví provádění kódu modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d1179-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d1179-104">Tato metoda není uvolnění prostředků na hostitele, uvolnění domény aplikace nebo zničit vlákna.</span><span class="sxs-lookup"><span data-stu-id="d1179-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="d1179-105">Musí být ukončen proces k uvolnění těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="d1179-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1179-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1179-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d1179-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d1179-107">Return Value</span></span>  
  
|<span data-ttu-id="d1179-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1179-108">HRESULT</span></span>|<span data-ttu-id="d1179-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d1179-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1179-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1179-110">S_OK</span></span>|<span data-ttu-id="d1179-111">`Stop` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d1179-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="d1179-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1179-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1179-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d1179-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1179-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1179-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1179-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d1179-115">The call timed out.</span></span>|  
|<span data-ttu-id="d1179-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1179-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1179-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d1179-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1179-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1179-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1179-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d1179-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1179-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1179-120">E_FAIL</span></span>|<span data-ttu-id="d1179-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d1179-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1179-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d1179-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1179-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1179-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1179-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1179-124">Requirements</span></span>  
 <span data-ttu-id="d1179-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1179-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1179-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1179-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1179-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1179-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1179-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1179-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1179-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1179-129">See also</span></span>
- [<span data-ttu-id="d1179-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1179-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
