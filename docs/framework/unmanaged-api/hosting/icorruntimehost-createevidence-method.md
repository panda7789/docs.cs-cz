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
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762315"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="61e3a-102">ICorRuntimeHost::CreateEvidence – metoda</span><span class="sxs-lookup"><span data-stu-id="61e3a-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="61e3a-103">Načte ukazatel rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , který umožňuje hostiteli vytvořit legitimaci zabezpečení, která bude předána metodě [CreateDomain –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [CreateDomainEx –](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="61e3a-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61e3a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61e3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61e3a-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="61e3a-106">mimo Ukazatel rozhraní, který <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> slouží k vytvoření legitimace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61e3a-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="61e3a-107">Tento ukazatel je typu `IUnknown` , takže volající by obvykle volali `QueryInterface` na toto rozhraní, aby získal ukazatel na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="61e3a-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61e3a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61e3a-108">Return Value</span></span>  
  
|<span data-ttu-id="61e3a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61e3a-109">HRESULT</span></span>|<span data-ttu-id="61e3a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="61e3a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61e3a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="61e3a-111">S_OK</span></span>|<span data-ttu-id="61e3a-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="61e3a-112">The operation was successful.</span></span>|  
|<span data-ttu-id="61e3a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="61e3a-113">S_FALSE</span></span>|<span data-ttu-id="61e3a-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="61e3a-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="61e3a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61e3a-115">E_FAIL</span></span>|<span data-ttu-id="61e3a-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="61e3a-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="61e3a-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="61e3a-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="61e3a-118">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="61e3a-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="61e3a-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61e3a-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61e3a-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="61e3a-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61e3a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61e3a-121">Remarks</span></span>  
 <span data-ttu-id="61e3a-122">Tato metoda vrací prázdnou kolekci, kterou nelze naplnit z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="61e3a-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="61e3a-123">Místo toho byste měli použít <xref:System.Security.Policy.Evidence> metodu.</span><span class="sxs-lookup"><span data-stu-id="61e3a-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e3a-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61e3a-124">Requirements</span></span>  
 <span data-ttu-id="61e3a-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e3a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e3a-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61e3a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61e3a-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="61e3a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61e3a-128">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="61e3a-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e3a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="61e3a-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="61e3a-130">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61e3a-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
