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
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139643"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="608fa-102">ICorRuntimeHost::CreateDomainSetup – metoda</span><span class="sxs-lookup"><span data-stu-id="608fa-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="608fa-103">Načte ukazatel rozhraní typu IAppDomainSetup – do instance <xref:System.AppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="608fa-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="608fa-104">`IAppDomainSetup` poskytuje metody pro konfiguraci aspektů aplikační domény před jejich vytvořením.</span><span class="sxs-lookup"><span data-stu-id="608fa-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="608fa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="608fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="608fa-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="608fa-107">mimo Ukazatel rozhraní na instanci <xref:System.AppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="608fa-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="608fa-108">Tento parametr je zadán jako `IUnknown`, takže volající by obecně měli volat `QueryInterface` na tomto ukazateli, aby získal ukazatel rozhraní typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="608fa-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="608fa-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="608fa-109">Return Value</span></span>  
  
|<span data-ttu-id="608fa-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="608fa-110">HRESULT</span></span>|<span data-ttu-id="608fa-111">Popis</span><span class="sxs-lookup"><span data-stu-id="608fa-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="608fa-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="608fa-112">S_OK</span></span>|<span data-ttu-id="608fa-113">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="608fa-113">The operation was successful.</span></span>|  
|<span data-ttu-id="608fa-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="608fa-114">S_FALSE</span></span>|<span data-ttu-id="608fa-115">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="608fa-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="608fa-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="608fa-116">E_FAIL</span></span>|<span data-ttu-id="608fa-117">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="608fa-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="608fa-118">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="608fa-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="608fa-119">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="608fa-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="608fa-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="608fa-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="608fa-121">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="608fa-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="608fa-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="608fa-122">Remarks</span></span>  
 <span data-ttu-id="608fa-123">Ukazatel vrácený z této metody je obvykle předán jako parametr metodě [CreateDomainEx –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="608fa-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="608fa-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="608fa-124">Requirements</span></span>  
 <span data-ttu-id="608fa-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="608fa-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="608fa-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="608fa-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="608fa-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="608fa-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="608fa-128">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="608fa-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608fa-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="608fa-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="608fa-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="608fa-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
