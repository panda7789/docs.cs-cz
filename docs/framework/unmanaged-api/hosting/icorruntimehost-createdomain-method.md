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
ms.openlocfilehash: 7c3e37fdb8a5afc973c913b1cfa56ab2e9f4fa52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127733"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="9e332-102">ICorRuntimeHost::CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="9e332-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="9e332-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e332-103">Creates an application domain.</span></span> <span data-ttu-id="9e332-104">Volající obdrží ukazatel rozhraní typu <xref:System._AppDomain> do instance typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e332-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e332-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e332-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e332-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e332-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="9e332-107">pro Volitelný parametr, který slouží k poskytnutí popisného názvu doméně.</span><span class="sxs-lookup"><span data-stu-id="9e332-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="9e332-108">Tento popisný název lze zobrazit v uživatelských rozhraních, jako jsou například ladicí programy, a identifikovat doménu.</span><span class="sxs-lookup"><span data-stu-id="9e332-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="9e332-109">pro Volitelné pole ukazatelů `IIdentity` instancí, které reprezentují legitimace namapované prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9e332-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="9e332-110">Objekt `IIdentity` lze získat voláním metody [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9e332-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="9e332-111">mimo Ukazatel rozhraní typu <xref:System._AppDomain> k instanci <xref:System.AppDomain?displayProperty=nameWithType>, kterou lze použít k další kontrole domény.</span><span class="sxs-lookup"><span data-stu-id="9e332-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e332-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e332-112">Return Value</span></span>  
  
|<span data-ttu-id="9e332-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e332-113">HRESULT</span></span>|<span data-ttu-id="9e332-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9e332-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e332-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e332-115">S_OK</span></span>|<span data-ttu-id="9e332-116">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9e332-116">The operation was successful.</span></span>|  
|<span data-ttu-id="9e332-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9e332-117">S_FALSE</span></span>|<span data-ttu-id="9e332-118">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="9e332-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9e332-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e332-119">E_FAIL</span></span>|<span data-ttu-id="9e332-120">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="9e332-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9e332-121">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="9e332-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9e332-122">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e332-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9e332-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e332-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e332-124">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9e332-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e332-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e332-125">Requirements</span></span>  
 <span data-ttu-id="9e332-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e332-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e332-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e332-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e332-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e332-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e332-129">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9e332-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e332-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e332-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="9e332-131">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e332-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
