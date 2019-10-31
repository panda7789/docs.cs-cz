---
title: ICorRuntimeHost::CreateDomainEx – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: a3a2d1827774ddedc00eb849f64256e3f425b3fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127715"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="50f26-102">ICorRuntimeHost::CreateDomainEx – metoda</span><span class="sxs-lookup"><span data-stu-id="50f26-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="50f26-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="50f26-103">Creates an application domain.</span></span> <span data-ttu-id="50f26-104">Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain>do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50f26-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50f26-105">Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené instance <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="50f26-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f26-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50f26-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50f26-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="50f26-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="50f26-108">pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně.</span><span class="sxs-lookup"><span data-stu-id="50f26-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="50f26-109">Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.</span><span class="sxs-lookup"><span data-stu-id="50f26-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="50f26-110">pro Volitelný ukazatel rozhraní typu `IAppDomainSetup`, získaný voláním metody [ICorRuntimeHost:: createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50f26-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="50f26-111">pro Volitelné pole ukazatelů `IIdentity` instancí, které reprezentují legitimace namapované prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="50f26-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="50f26-112">Objekt `IIdentity` lze získat voláním metody [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50f26-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="50f26-113">mimo Ukazatel rozhraní typu <xref:System._AppDomain> k instanci <xref:System.AppDomain?displayProperty=nameWithType>, kterou lze použít k další kontrole domény.</span><span class="sxs-lookup"><span data-stu-id="50f26-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f26-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50f26-114">Return Value</span></span>  
  
|<span data-ttu-id="50f26-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50f26-115">HRESULT</span></span>|<span data-ttu-id="50f26-116">Popis</span><span class="sxs-lookup"><span data-stu-id="50f26-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50f26-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="50f26-117">S_OK</span></span>|<span data-ttu-id="50f26-118">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="50f26-118">The operation was successful.</span></span>|  
|<span data-ttu-id="50f26-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="50f26-119">S_FALSE</span></span>|<span data-ttu-id="50f26-120">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="50f26-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="50f26-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50f26-121">E_FAIL</span></span>|<span data-ttu-id="50f26-122">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="50f26-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="50f26-123">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="50f26-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="50f26-124">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50f26-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50f26-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50f26-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50f26-126">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="50f26-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f26-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50f26-127">Remarks</span></span>  
 <span data-ttu-id="50f26-128">`CreateDomainEx` rozšiřuje možnosti [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volajícímu předává instanci `IAppDomainSetup` s hodnotami vlastností pro konfiguraci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="50f26-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f26-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50f26-129">Requirements</span></span>  
 <span data-ttu-id="50f26-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50f26-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f26-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50f26-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50f26-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="50f26-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50f26-133">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="50f26-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f26-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50f26-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="50f26-135">CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="50f26-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="50f26-136">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50f26-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
