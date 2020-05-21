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
ms.openlocfilehash: aa1ce70311cd4ef0204c1c31efee8bd7b313c81d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762328"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="e0390-102">ICorRuntimeHost::CreateDomainSetup – metoda</span><span class="sxs-lookup"><span data-stu-id="e0390-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="e0390-103">Načte ukazatel rozhraní typu IAppDomainSetup – do <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="e0390-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="e0390-104">`IAppDomainSetup`poskytuje metody pro konfiguraci aspektů aplikační domény před jejich vytvořením.</span><span class="sxs-lookup"><span data-stu-id="e0390-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0390-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0390-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0390-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0390-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="e0390-107">mimo Ukazatel rozhraní na <xref:System.AppDomainSetup?displayProperty=nameWithType> instanci.</span><span class="sxs-lookup"><span data-stu-id="e0390-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="e0390-108">Tento parametr je typu `IUnknown` , takže volající by obecně volali `QueryInterface` Tento ukazatel, aby získal ukazatel rozhraní typu `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="e0390-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0390-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0390-109">Return Value</span></span>  
  
|<span data-ttu-id="e0390-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0390-110">HRESULT</span></span>|<span data-ttu-id="e0390-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e0390-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0390-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0390-112">S_OK</span></span>|<span data-ttu-id="e0390-113">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e0390-113">The operation was successful.</span></span>|  
|<span data-ttu-id="e0390-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e0390-114">S_FALSE</span></span>|<span data-ttu-id="e0390-115">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="e0390-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e0390-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0390-116">E_FAIL</span></span>|<span data-ttu-id="e0390-117">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="e0390-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e0390-118">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="e0390-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e0390-119">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0390-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0390-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0390-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0390-121">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e0390-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0390-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0390-122">Remarks</span></span>  
 <span data-ttu-id="e0390-123">Ukazatel vrácený z této metody je obvykle předán jako parametr metodě [CreateDomainEx –](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0390-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0390-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0390-124">Requirements</span></span>  
 <span data-ttu-id="e0390-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0390-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0390-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0390-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0390-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0390-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0390-128">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e0390-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0390-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0390-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="e0390-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0390-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
