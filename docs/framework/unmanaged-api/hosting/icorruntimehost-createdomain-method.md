---
title: ICorRuntimeHost::CreateDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdacb690b31e7b9930825e5d54ef8fc95bb3a5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762128"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="0a8aa-102">ICorRuntimeHost::CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0a8aa-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="0a8aa-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-103">Creates an application domain.</span></span> <span data-ttu-id="0a8aa-104">Volající přijímá ukazatel rozhraní typu <xref:System._AppDomain> do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a8aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a8aa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a8aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a8aa-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="0a8aa-107">[in] Volitelný parametr, který slouží k pojmenování k doméně popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="0a8aa-108">Tento popisný název lze zobrazit v uživatelských rozhraních, jako je například ladicí programy k identifikaci domény.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="0a8aa-109">[in] Volitelné pole ukazatelů na `IIdentity` instancí, které představují důkazy mapovaný prostřednictvím zásad zabezpečení sadu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="0a8aa-110">`IIdentity` Objektu lze získat voláním [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="0a8aa-111">[out] Ukazatel rozhraní typu <xref:System._AppDomain> do instance <xref:System.AppDomain?displayProperty=nameWithType> , který slouží k podrobnějšímu řízení domény.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a8aa-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a8aa-112">Return Value</span></span>  
  
|<span data-ttu-id="0a8aa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a8aa-113">HRESULT</span></span>|<span data-ttu-id="0a8aa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0a8aa-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a8aa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a8aa-115">S_OK</span></span>|<span data-ttu-id="0a8aa-116">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-116">The operation was successful.</span></span>|  
|<span data-ttu-id="0a8aa-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0a8aa-117">S_FALSE</span></span>|<span data-ttu-id="0a8aa-118">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0a8aa-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a8aa-119">E_FAIL</span></span>|<span data-ttu-id="0a8aa-120">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0a8aa-121">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0a8aa-122">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0a8aa-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a8aa-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a8aa-124">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0a8aa-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a8aa-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a8aa-125">Requirements</span></span>  
 <span data-ttu-id="0a8aa-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a8aa-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a8aa-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a8aa-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a8aa-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a8aa-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a8aa-129">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0a8aa-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8aa-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a8aa-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0a8aa-131">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a8aa-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
