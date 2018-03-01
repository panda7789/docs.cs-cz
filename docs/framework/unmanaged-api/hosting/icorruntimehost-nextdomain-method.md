---
title: "ICorRuntimeHost::NextDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e539cd4071fe9713ed53f66c2f67b24b787d259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="ea90e-102">ICorRuntimeHost::NextDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="ea90e-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="ea90e-103">Získá ukazatele rozhraní do další domény ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="ea90e-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea90e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea90e-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea90e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea90e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ea90e-106">[v] Enumerátor, který byl získán pomocí volání [enumdomains –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="ea90e-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ea90e-107">[out] Ukazatele rozhraní na <xref:System._AppDomain?displayProperty=nameWithType> typ, který představuje další domény ve výčtu, nebo hodnota null, pokud neexistuje žádné další domény.</span><span class="sxs-lookup"><span data-stu-id="ea90e-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea90e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea90e-108">Return Value</span></span>  
  
|<span data-ttu-id="ea90e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea90e-109">HRESULT</span></span>|<span data-ttu-id="ea90e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ea90e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea90e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea90e-111">S_OK</span></span>|<span data-ttu-id="ea90e-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ea90e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="ea90e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ea90e-113">S_FALSE</span></span>|<span data-ttu-id="ea90e-114">Nepodařilo se dokončit operaci, nebo nejsou žádné další domény ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="ea90e-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="ea90e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea90e-115">E_FAIL</span></span>|<span data-ttu-id="ea90e-116">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="ea90e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ea90e-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="ea90e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ea90e-118">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea90e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ea90e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea90e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea90e-120">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ea90e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea90e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea90e-121">Requirements</span></span>  
 <span data-ttu-id="ea90e-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea90e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea90e-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea90e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea90e-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea90e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea90e-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ea90e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea90e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea90e-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="ea90e-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea90e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
