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
ms.openlocfilehash: 545af69e06e7ea4262450025e9cb0d6529f99ad4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780063"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="cb91e-102">ICorRuntimeHost::EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="cb91e-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="cb91e-103">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="cb91e-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb91e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb91e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb91e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb91e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="cb91e-106">[out] Enumerátor pro domény.</span><span class="sxs-lookup"><span data-stu-id="cb91e-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb91e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cb91e-107">Return Value</span></span>  
  
|<span data-ttu-id="cb91e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb91e-108">HRESULT</span></span>|<span data-ttu-id="cb91e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb91e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb91e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb91e-110">S_OK</span></span>|<span data-ttu-id="cb91e-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="cb91e-111">The operation was successful.</span></span>|  
|<span data-ttu-id="cb91e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cb91e-112">S_FALSE</span></span>|<span data-ttu-id="cb91e-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="cb91e-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cb91e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb91e-114">E_FAIL</span></span>|<span data-ttu-id="cb91e-115">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="cb91e-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cb91e-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="cb91e-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cb91e-117">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb91e-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb91e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb91e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb91e-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cb91e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb91e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb91e-120">Requirements</span></span>  
 <span data-ttu-id="cb91e-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb91e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb91e-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb91e-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb91e-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb91e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb91e-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="cb91e-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb91e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb91e-125">See also</span></span>

- [<span data-ttu-id="cb91e-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb91e-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
