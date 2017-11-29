---
title: "ICorRuntimeHost::CreateEvidence – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateEvidence
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c050d8d610b32d2e8421a5d61e36cee151085e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="7d525-102">ICorRuntimeHost::CreateEvidence – metoda</span><span class="sxs-lookup"><span data-stu-id="7d525-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="7d525-103">Získá ukazatele rozhraní typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, což umožňuje na hostiteli a poté vytvořit důkaz zabezpečení mají být předány [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7d525-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d525-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d525-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d525-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d525-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="7d525-106">[out] Ukazatel rozhraní <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance použitý k vytvoření důkaz zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7d525-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="7d525-107">Tento ukazatel je zadán `IUnknown`, takže volající by měly volat obvykle `QueryInterface` na tomto rozhraní k získání ukazatele na <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d525-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d525-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d525-108">Return Value</span></span>  
  
|<span data-ttu-id="7d525-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d525-109">HRESULT</span></span>|<span data-ttu-id="7d525-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7d525-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d525-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d525-111">S_OK</span></span>|<span data-ttu-id="7d525-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7d525-112">The operation was successful.</span></span>|  
|<span data-ttu-id="7d525-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7d525-113">S_FALSE</span></span>|<span data-ttu-id="7d525-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="7d525-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7d525-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d525-115">E_FAIL</span></span>|<span data-ttu-id="7d525-116">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="7d525-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7d525-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="7d525-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7d525-118">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d525-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d525-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d525-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d525-120">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7d525-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d525-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d525-121">Remarks</span></span>  
 <span data-ttu-id="7d525-122">Tato metoda vrátí prázdnou kolekci, která nelze načíst z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7d525-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="7d525-123">Měli byste použít <xref:System.Security.Policy.Evidence> metoda místo.</span><span class="sxs-lookup"><span data-stu-id="7d525-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d525-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d525-124">Requirements</span></span>  
 <span data-ttu-id="7d525-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d525-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d525-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d525-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d525-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d525-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d525-128">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="7d525-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d525-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d525-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="7d525-130">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d525-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
