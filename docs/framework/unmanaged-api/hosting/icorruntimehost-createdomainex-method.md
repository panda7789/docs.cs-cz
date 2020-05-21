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
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762341"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="a1b34-102">ICorRuntimeHost::CreateDomainEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a1b34-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="a1b34-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1b34-103">Creates an application domain.</span></span> <span data-ttu-id="a1b34-104">Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a1b34-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1b34-105">Tato metoda umožňuje volajícímu předat instanci IAppDomainSetup – ke konfiguraci dalších funkcí vrácené <xref:System._AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="a1b34-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b34-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b34-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1b34-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1b34-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="a1b34-108">pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně.</span><span class="sxs-lookup"><span data-stu-id="a1b34-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="a1b34-109">Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.</span><span class="sxs-lookup"><span data-stu-id="a1b34-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="a1b34-110">pro Volitelný ukazatel rozhraní typu `IAppDomainSetup` , získaný voláním metody [ICorRuntimeHost:: createdomainsetup –](icorruntimehost-createdomainsetup-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a1b34-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="a1b34-111">pro Volitelné pole ukazatelů na `IIdentity` instance, které reprezentují legitimace namapované prostřednictvím zásad zabezpečení, aby bylo možné vytvořit sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="a1b34-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="a1b34-112">`IIdentity`Objekt lze získat voláním metody [createevidence –](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a1b34-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a1b34-113">mimo Ukazatel rozhraní typu <xref:System._AppDomain> na instanci <xref:System.AppDomain?displayProperty=nameWithType> , která může být použita k další kontrole domény.</span><span class="sxs-lookup"><span data-stu-id="a1b34-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1b34-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a1b34-114">Return Value</span></span>  
  
|<span data-ttu-id="a1b34-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1b34-115">HRESULT</span></span>|<span data-ttu-id="a1b34-116">Popis</span><span class="sxs-lookup"><span data-stu-id="a1b34-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1b34-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1b34-117">S_OK</span></span>|<span data-ttu-id="a1b34-118">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a1b34-118">The operation was successful.</span></span>|  
|<span data-ttu-id="a1b34-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a1b34-119">S_FALSE</span></span>|<span data-ttu-id="a1b34-120">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="a1b34-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a1b34-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1b34-121">E_FAIL</span></span>|<span data-ttu-id="a1b34-122">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="a1b34-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a1b34-123">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="a1b34-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a1b34-124">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1b34-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a1b34-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1b34-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1b34-126">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a1b34-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1b34-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1b34-127">Remarks</span></span>  
 <span data-ttu-id="a1b34-128">`CreateDomainEx`rozšiřuje možnosti [CreateDomain –](icorruntimehost-createdomain-method.md) tím, že umožňuje volajícímu předat `IAppDomainSetup` instanci s hodnotami vlastností pro konfiguraci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1b34-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b34-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1b34-129">Requirements</span></span>  
 <span data-ttu-id="a1b34-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b34-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b34-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1b34-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1b34-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1b34-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1b34-133">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a1b34-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b34-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1b34-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="a1b34-135">CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a1b34-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="a1b34-136">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1b34-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
