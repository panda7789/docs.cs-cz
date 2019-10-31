---
title: ICorRuntimeHost::CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: e2eddfab68e5c9e2ebffe2c96c9348f3cd799c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127753"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="5d6ae-102">ICorRuntimeHost::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="5d6ae-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="5d6ae-103">Obnoví enumerátor domény zpátky na začátek seznamu domén.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d6ae-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d6ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d6ae-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="5d6ae-106">pro Enumerátor, který má být resetován.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d6ae-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d6ae-107">Return Value</span></span>  
  
|<span data-ttu-id="5d6ae-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d6ae-108">HRESULT</span></span>|<span data-ttu-id="5d6ae-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5d6ae-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d6ae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d6ae-110">S_OK</span></span>|<span data-ttu-id="5d6ae-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-111">The operation was successful.</span></span>|  
|<span data-ttu-id="5d6ae-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5d6ae-112">S_FALSE</span></span>|<span data-ttu-id="5d6ae-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5d6ae-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d6ae-114">E_FAIL</span></span>|<span data-ttu-id="5d6ae-115">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5d6ae-116">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5d6ae-117">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5d6ae-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d6ae-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d6ae-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5d6ae-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d6ae-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d6ae-120">Requirements</span></span>  
 <span data-ttu-id="5d6ae-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d6ae-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d6ae-122">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d6ae-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d6ae-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d6ae-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d6ae-124">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5d6ae-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6ae-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d6ae-125">See also</span></span>

- [<span data-ttu-id="5d6ae-126">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="5d6ae-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="5d6ae-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d6ae-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
