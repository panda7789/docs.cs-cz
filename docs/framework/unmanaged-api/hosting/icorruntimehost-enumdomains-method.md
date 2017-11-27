---
title: "ICorRuntimeHost::EnumDomains – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c63e4345815a073fe6aa422018b6fadf45bd5370
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="7aea0-102">ICorRuntimeHost::EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="7aea0-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="7aea0-103">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="7aea0-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aea0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aea0-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7aea0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aea0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="7aea0-106">[out] Enumerátor pro domény.</span><span class="sxs-lookup"><span data-stu-id="7aea0-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7aea0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7aea0-107">Return Value</span></span>  
  
|<span data-ttu-id="7aea0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7aea0-108">HRESULT</span></span>|<span data-ttu-id="7aea0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7aea0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7aea0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7aea0-110">S_OK</span></span>|<span data-ttu-id="7aea0-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7aea0-111">The operation was successful.</span></span>|  
|<span data-ttu-id="7aea0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7aea0-112">S_FALSE</span></span>|<span data-ttu-id="7aea0-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="7aea0-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7aea0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7aea0-114">E_FAIL</span></span>|<span data-ttu-id="7aea0-115">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="7aea0-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7aea0-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="7aea0-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7aea0-117">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7aea0-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7aea0-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7aea0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7aea0-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7aea0-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7aea0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7aea0-120">Requirements</span></span>  
 <span data-ttu-id="7aea0-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aea0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aea0-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7aea0-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7aea0-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7aea0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7aea0-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="7aea0-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aea0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aea0-125">See Also</span></span>  
 [<span data-ttu-id="7aea0-126">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7aea0-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
