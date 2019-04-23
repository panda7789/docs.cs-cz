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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a538f14e7dbf24a94343f364201e968bffa757f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158922"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="75c64-102">ICorRuntimeHost::CreateDomainEx – metoda</span><span class="sxs-lookup"><span data-stu-id="75c64-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="75c64-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="75c64-103">Creates an application domain.</span></span> <span data-ttu-id="75c64-104">Volající přijímá ukazatel rozhraní, typu <xref:System._AppDomain>, do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75c64-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75c64-105">Tato metoda umožňuje volajícímu předejte instanci iappdomainsetup – ke konfiguraci dalších funkcí vráceného <xref:System._AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="75c64-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c64-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75c64-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75c64-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="75c64-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="75c64-108">[in] Volitelný parametr, který slouží k pojmenování k doméně popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="75c64-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="75c64-109">Tento popisný název lze zobrazit v uživatelských rozhraních, jako je například ladicí programy k identifikaci domény.</span><span class="sxs-lookup"><span data-stu-id="75c64-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="75c64-110">[in] Ukazatel volitelné rozhraní typu `IAppDomainSetup`, získaný voláním [icorruntimehost::createdomainsetup –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="75c64-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="75c64-111">[in] Volitelné pole ukazatelů na `IIdentity` instancí, které představují důkazy mapovaný prostřednictvím zásad zabezpečení sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="75c64-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="75c64-112">`IIdentity` Objektu lze získat voláním [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="75c64-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="75c64-113">[out] Ukazatel rozhraní typu <xref:System._AppDomain> do instance <xref:System.AppDomain?displayProperty=nameWithType> , který slouží k podrobnějšímu řízení domény.</span><span class="sxs-lookup"><span data-stu-id="75c64-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75c64-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75c64-114">Return Value</span></span>  
  
|<span data-ttu-id="75c64-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75c64-115">HRESULT</span></span>|<span data-ttu-id="75c64-116">Popis</span><span class="sxs-lookup"><span data-stu-id="75c64-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75c64-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="75c64-117">S_OK</span></span>|<span data-ttu-id="75c64-118">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="75c64-118">The operation was successful.</span></span>|  
|<span data-ttu-id="75c64-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="75c64-119">S_FALSE</span></span>|<span data-ttu-id="75c64-120">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="75c64-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="75c64-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="75c64-121">E_FAIL</span></span>|<span data-ttu-id="75c64-122">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="75c64-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="75c64-123">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="75c64-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="75c64-124">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="75c64-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="75c64-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="75c64-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="75c64-126">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="75c64-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75c64-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75c64-127">Remarks</span></span>  
 <span data-ttu-id="75c64-128">`CreateDomainEx` rozšiřuje možnosti [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) tím, že volající a zajistěte tak předání `IAppDomainSetup` instance s hodnotami vlastností konfigurace domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="75c64-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c64-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75c64-129">Requirements</span></span>  
 <span data-ttu-id="75c64-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75c64-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75c64-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75c64-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75c64-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75c64-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75c64-133">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="75c64-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c64-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75c64-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="75c64-135">CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="75c64-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="75c64-136">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75c64-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
