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
ms.openlocfilehash: bf3aff2c3c4d10c4ee805a6110561d6fdcd63a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437983"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="0c909-102">ICorRuntimeHost::CreateDomainSetup – metoda</span><span class="sxs-lookup"><span data-stu-id="0c909-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="0c909-103">Získá typ ukazatele rozhraní z iappdomainsetup – k <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="0c909-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="0c909-104">`IAppDomainSetup` poskytuje metody pro konfiguraci aspektů domény aplikace předtím, než se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="0c909-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c909-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c909-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c909-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c909-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="0c909-107">[out] Ukazatele rozhraní k <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="0c909-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="0c909-108">Tento parametr je zadán jako `IUnknown`, takže volající by měly volat obecně `QueryInterface` na tento ukazatel k získání ukazatele rozhraní typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="0c909-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c909-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c909-109">Return Value</span></span>  
  
|<span data-ttu-id="0c909-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c909-110">HRESULT</span></span>|<span data-ttu-id="0c909-111">Popis</span><span class="sxs-lookup"><span data-stu-id="0c909-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c909-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c909-112">S_OK</span></span>|<span data-ttu-id="0c909-113">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0c909-113">The operation was successful.</span></span>|  
|<span data-ttu-id="0c909-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0c909-114">S_FALSE</span></span>|<span data-ttu-id="0c909-115">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="0c909-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0c909-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c909-116">E_FAIL</span></span>|<span data-ttu-id="0c909-117">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="0c909-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0c909-118">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="0c909-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0c909-119">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c909-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c909-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c909-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c909-121">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0c909-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c909-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c909-122">Remarks</span></span>  
 <span data-ttu-id="0c909-123">Tato metoda vrátí ukazatele se obvykle předá jako parametr, který se [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0c909-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c909-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c909-124">Requirements</span></span>  
 <span data-ttu-id="0c909-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c909-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c909-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c909-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c909-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c909-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c909-128">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0c909-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c909-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c909-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="0c909-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c909-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
