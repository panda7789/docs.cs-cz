---
title: ICorRuntimeHost::CreateDomainSetup – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2758deaabf9db1cbc5465eb9b5976add534e87b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469662"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="95d35-102">ICorRuntimeHost::CreateDomainSetup – metoda</span><span class="sxs-lookup"><span data-stu-id="95d35-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="95d35-103">Získá ukazatel rozhraní z zadejte iappdomainsetup – pro <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="95d35-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="95d35-104">`IAppDomainSetup` poskytuje metody pro konfiguraci aspektů doménu aplikace před jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="95d35-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d35-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95d35-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="95d35-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="95d35-107">[out] Ukazatel rozhraní k <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="95d35-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="95d35-108">Tento parametr zadán jako `IUnknown`, takže obecně by měly volat volající `QueryInterface` pro tento ukazatel na ukazatel rozhraní typu získat `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="95d35-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95d35-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95d35-109">Return Value</span></span>  
  
|<span data-ttu-id="95d35-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95d35-110">HRESULT</span></span>|<span data-ttu-id="95d35-111">Popis</span><span class="sxs-lookup"><span data-stu-id="95d35-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95d35-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="95d35-112">S_OK</span></span>|<span data-ttu-id="95d35-113">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="95d35-113">The operation was successful.</span></span>|  
|<span data-ttu-id="95d35-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="95d35-114">S_FALSE</span></span>|<span data-ttu-id="95d35-115">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="95d35-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="95d35-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95d35-116">E_FAIL</span></span>|<span data-ttu-id="95d35-117">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="95d35-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="95d35-118">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="95d35-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="95d35-119">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95d35-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95d35-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95d35-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95d35-121">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="95d35-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d35-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95d35-122">Remarks</span></span>  
 <span data-ttu-id="95d35-123">Tato metoda vrátí ukazatel je obvykle předán jako parametr, který se [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="95d35-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d35-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95d35-124">Requirements</span></span>  
 <span data-ttu-id="95d35-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d35-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d35-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95d35-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95d35-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95d35-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95d35-128">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="95d35-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d35-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95d35-129">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="95d35-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95d35-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
