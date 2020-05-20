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
ms.openlocfilehash: 55cd444ffedc92ba74239421ae548ffd930e6ab7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703940"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="8c3ce-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="8c3ce-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="8c3ce-103">Zastaví provádění kódu modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8c3ce-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8c3ce-104">Tato metoda neuvolní prostředky do hostitele, uvolní aplikační domény nebo zničí vlákna.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="8c3ce-105">Aby bylo možné uvolnit tyto prostředky, je nutné ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3ce-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c3ce-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8c3ce-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c3ce-107">Return Value</span></span>  
  
|<span data-ttu-id="8c3ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c3ce-108">HRESULT</span></span>|<span data-ttu-id="8c3ce-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8c3ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c3ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c3ce-110">S_OK</span></span>|<span data-ttu-id="8c3ce-111">`Stop`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="8c3ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c3ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c3ce-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c3ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c3ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c3ce-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="8c3ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c3ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c3ce-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c3ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c3ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c3ce-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c3ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c3ce-120">E_FAIL</span></span>|<span data-ttu-id="8c3ce-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c3ce-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c3ce-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c3ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c3ce-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c3ce-124">Requirements</span></span>  
 <span data-ttu-id="8c3ce-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3ce-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3ce-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c3ce-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c3ce-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c3ce-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c3ce-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3ce-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3ce-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c3ce-129">See also</span></span>

- [<span data-ttu-id="8c3ce-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c3ce-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
