---
title: ICLRErrorReportingManager::EndCustomDump – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c2d2e5454a26111748f9676cfe1ce5caa76cad5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772848"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="aaa61-102">ICLRErrorReportingManager::EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="aaa61-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="aaa61-103">Odstraní konfiguraci vlastních zásobníku s výpisem paměti, který byl zadán v dřívějším volání [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aaa61-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa61-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aaa61-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aaa61-105">Return Value</span></span>  
  
|<span data-ttu-id="aaa61-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaa61-106">HRESULT</span></span>|<span data-ttu-id="aaa61-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aaa61-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aaa61-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aaa61-108">S_OK</span></span>|<span data-ttu-id="aaa61-109">`EndCustomDump` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="aaa61-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="aaa61-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aaa61-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aaa61-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aaa61-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aaa61-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aaa61-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aaa61-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="aaa61-113">The call timed out.</span></span>|  
|<span data-ttu-id="aaa61-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aaa61-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aaa61-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="aaa61-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aaa61-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aaa61-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aaa61-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="aaa61-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aaa61-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aaa61-118">E_FAIL</span></span>|<span data-ttu-id="aaa61-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="aaa61-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aaa61-120">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="aaa61-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aaa61-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aaa61-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa61-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaa61-122">Remarks</span></span>  
 <span data-ttu-id="aaa61-123">`EndCustomDump` Metoda vymaže konfigurační s výpisem paměti zásobníku vlastní sadu v dřívějším volání `BeginCustomDump` metoda a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="aaa61-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="aaa61-124">By měla být volána po dokončení výpis vlastní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aaa61-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aaa61-125">Nepodařilo se zavolat `EndCustomDump` způsobí, že k únik paměti.</span><span class="sxs-lookup"><span data-stu-id="aaa61-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa61-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaa61-126">Requirements</span></span>  
 <span data-ttu-id="aaa61-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa61-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa61-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aaa61-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aaa61-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaa61-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aaa61-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa61-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa61-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaa61-131">See also</span></span>

- [<span data-ttu-id="aaa61-132">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="aaa61-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="aaa61-133">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="aaa61-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="aaa61-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaa61-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
