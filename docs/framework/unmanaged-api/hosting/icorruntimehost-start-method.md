---
title: ICorRuntimeHost::Start – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: c450d83669a3bc548c15ed5800dc73438b9a84a6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127683"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="12c3b-102">ICorRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="12c3b-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="12c3b-103">Spustí modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="12c3b-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c3b-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="12c3b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12c3b-105">Return Value</span></span>  
  
|<span data-ttu-id="12c3b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12c3b-106">HRESULT</span></span>|<span data-ttu-id="12c3b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="12c3b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12c3b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="12c3b-108">S_OK</span></span>|<span data-ttu-id="12c3b-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="12c3b-109">The operation was successful.</span></span>|  
|<span data-ttu-id="12c3b-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="12c3b-110">S_FALSE</span></span>|<span data-ttu-id="12c3b-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="12c3b-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="12c3b-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12c3b-112">E_FAIL</span></span>|<span data-ttu-id="12c3b-113">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="12c3b-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="12c3b-114">Pokud metoda vrátí E_FAIL, CLR již není v procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="12c3b-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="12c3b-115">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="12c3b-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="12c3b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12c3b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12c3b-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="12c3b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12c3b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12c3b-118">Remarks</span></span>  
 <span data-ttu-id="12c3b-119">Obvykle není nutné volat metodu `Start`, protože CLR se spustí automaticky při prvním požadavku na spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="12c3b-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c3b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12c3b-120">Requirements</span></span>  
 <span data-ttu-id="12c3b-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c3b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c3b-122">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="12c3b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12c3b-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12c3b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12c3b-124">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="12c3b-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c3b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12c3b-125">See also</span></span>

- [<span data-ttu-id="12c3b-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12c3b-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
