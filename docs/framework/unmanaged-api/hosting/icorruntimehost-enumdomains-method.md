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
ms.openlocfilehash: 8e4db2330c6d46610bbb3da8b732b1c098659c97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729077"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="faf63-102">ICorRuntimeHost::EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="faf63-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="faf63-103">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="faf63-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faf63-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="faf63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="faf63-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="faf63-106">[out] Enumerátor pro domény.</span><span class="sxs-lookup"><span data-stu-id="faf63-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faf63-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="faf63-107">Return Value</span></span>  
  
|<span data-ttu-id="faf63-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faf63-108">HRESULT</span></span>|<span data-ttu-id="faf63-109">Popis</span><span class="sxs-lookup"><span data-stu-id="faf63-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="faf63-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="faf63-110">S_OK</span></span>|<span data-ttu-id="faf63-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="faf63-111">The operation was successful.</span></span>|  
|<span data-ttu-id="faf63-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="faf63-112">S_FALSE</span></span>|<span data-ttu-id="faf63-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="faf63-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="faf63-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="faf63-114">E_FAIL</span></span>|<span data-ttu-id="faf63-115">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="faf63-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="faf63-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="faf63-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="faf63-117">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="faf63-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="faf63-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="faf63-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="faf63-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="faf63-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faf63-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="faf63-120">Requirements</span></span>  
 <span data-ttu-id="faf63-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf63-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf63-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="faf63-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faf63-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="faf63-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faf63-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="faf63-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf63-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faf63-125">See also</span></span>
- [<span data-ttu-id="faf63-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="faf63-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
