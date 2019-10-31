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
ms.openlocfilehash: e5a1642f968228c5815732ecd470cb8f02a0eb83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139580"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="227c4-102">ICorRuntimeHost::EnumDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="227c4-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="227c4-103">Získá enumerátor pro domény v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="227c4-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="227c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="227c4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="227c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="227c4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="227c4-106">mimo Enumerátor pro domény.</span><span class="sxs-lookup"><span data-stu-id="227c4-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="227c4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="227c4-107">Return Value</span></span>  
  
|<span data-ttu-id="227c4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="227c4-108">HRESULT</span></span>|<span data-ttu-id="227c4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="227c4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="227c4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="227c4-110">S_OK</span></span>|<span data-ttu-id="227c4-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="227c4-111">The operation was successful.</span></span>|  
|<span data-ttu-id="227c4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="227c4-112">S_FALSE</span></span>|<span data-ttu-id="227c4-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="227c4-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="227c4-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="227c4-114">E_FAIL</span></span>|<span data-ttu-id="227c4-115">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="227c4-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="227c4-116">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="227c4-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="227c4-117">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="227c4-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="227c4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="227c4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="227c4-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="227c4-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="227c4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="227c4-120">Requirements</span></span>  
 <span data-ttu-id="227c4-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="227c4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="227c4-122">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="227c4-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="227c4-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="227c4-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="227c4-124">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="227c4-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="227c4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="227c4-125">See also</span></span>

- [<span data-ttu-id="227c4-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="227c4-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
