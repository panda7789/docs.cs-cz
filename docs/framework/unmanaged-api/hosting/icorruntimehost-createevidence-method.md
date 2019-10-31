---
title: ICorRuntimeHost::CreateEvidence – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 429ce0510162b3256cdf58f4820b04dd80243e29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139631"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="1a847-102">ICorRuntimeHost::CreateEvidence – metoda</span><span class="sxs-lookup"><span data-stu-id="1a847-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="1a847-103">Získá ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána metodě [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a847-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a847-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a847-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a847-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a847-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="1a847-106">mimo Ukazatel rozhraní na instanci <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, která se používá k vytvoření legitimace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1a847-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="1a847-107">Tento ukazatel je typu `IUnknown`, takže volající by obvykle měli volat `QueryInterface` na tomto rozhraní, aby získal ukazatel na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a847-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a847-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a847-108">Return Value</span></span>  
  
|<span data-ttu-id="1a847-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a847-109">HRESULT</span></span>|<span data-ttu-id="1a847-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1a847-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a847-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a847-111">S_OK</span></span>|<span data-ttu-id="1a847-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="1a847-112">The operation was successful.</span></span>|  
|<span data-ttu-id="1a847-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a847-113">S_FALSE</span></span>|<span data-ttu-id="1a847-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="1a847-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1a847-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a847-115">E_FAIL</span></span>|<span data-ttu-id="1a847-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="1a847-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1a847-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="1a847-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1a847-118">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1a847-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1a847-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a847-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a847-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1a847-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a847-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a847-121">Remarks</span></span>  
 <span data-ttu-id="1a847-122">Tato metoda vrací prázdnou kolekci, kterou nelze naplnit z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="1a847-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="1a847-123">Místo toho byste měli použít metodu <xref:System.Security.Policy.Evidence>.</span><span class="sxs-lookup"><span data-stu-id="1a847-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a847-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a847-124">Requirements</span></span>  
 <span data-ttu-id="1a847-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a847-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a847-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a847-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a847-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a847-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a847-128">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1a847-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a847-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a847-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1a847-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a847-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
