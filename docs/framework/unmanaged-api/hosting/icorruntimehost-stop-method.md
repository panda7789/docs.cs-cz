---
title: ICorRuntimeHost::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca51b87e7afc8e9e48d541a32b3bd60a19a5ff70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965970"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="b31c7-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="b31c7-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="b31c7-103">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="b31c7-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b31c7-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b31c7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b31c7-105">Return Value</span></span>  
  
|<span data-ttu-id="b31c7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b31c7-106">HRESULT</span></span>|<span data-ttu-id="b31c7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b31c7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b31c7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b31c7-108">S_OK</span></span>|<span data-ttu-id="b31c7-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b31c7-109">The operation was successful.</span></span>|  
|<span data-ttu-id="b31c7-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b31c7-110">S_FALSE</span></span>|<span data-ttu-id="b31c7-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="b31c7-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b31c7-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b31c7-112">E_FAIL</span></span>|<span data-ttu-id="b31c7-113">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="b31c7-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b31c7-114">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="b31c7-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b31c7-115">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b31c7-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b31c7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b31c7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b31c7-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b31c7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b31c7-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b31c7-118">Remarks</span></span>  
 <span data-ttu-id="b31c7-119">Obvykle není nutné volat `Stop` metodu, protože kód se zastaví, když se proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="b31c7-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b31c7-120">Po volání do `Stop`nástroje nelze modul CLR znovu inicializovat do stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="b31c7-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b31c7-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b31c7-121">Requirements</span></span>  
 <span data-ttu-id="b31c7-122">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b31c7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b31c7-123">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b31c7-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b31c7-124">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b31c7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b31c7-125">**Verze .NET Framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b31c7-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b31c7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b31c7-126">See also</span></span>

- [<span data-ttu-id="b31c7-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b31c7-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
