---
title: ICorRuntimeHost::EnumDomains – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 688e7a0fa32650aa0f626ddf40283f73ceb57156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437788"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="dc476-102">ICorRuntimeHost::EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="dc476-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="dc476-103">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="dc476-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc476-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc476-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc476-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc476-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="dc476-106">[out] Enumerátor pro domény.</span><span class="sxs-lookup"><span data-stu-id="dc476-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc476-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc476-107">Return Value</span></span>  
  
|<span data-ttu-id="dc476-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc476-108">HRESULT</span></span>|<span data-ttu-id="dc476-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dc476-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc476-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc476-110">S_OK</span></span>|<span data-ttu-id="dc476-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="dc476-111">The operation was successful.</span></span>|  
|<span data-ttu-id="dc476-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dc476-112">S_FALSE</span></span>|<span data-ttu-id="dc476-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="dc476-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="dc476-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc476-114">E_FAIL</span></span>|<span data-ttu-id="dc476-115">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="dc476-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dc476-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="dc476-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="dc476-117">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dc476-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dc476-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc476-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc476-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dc476-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc476-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc476-120">Requirements</span></span>  
 <span data-ttu-id="dc476-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc476-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc476-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc476-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc476-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc476-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc476-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="dc476-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc476-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc476-125">See Also</span></span>  
 [<span data-ttu-id="dc476-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc476-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
