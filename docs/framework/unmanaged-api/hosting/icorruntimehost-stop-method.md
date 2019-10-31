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
ms.openlocfilehash: 5fcf8bc861b2ef0b8ea9f5a5e46585564cc26615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127706"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="4baf1-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="4baf1-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="4baf1-103">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="4baf1-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4baf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4baf1-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4baf1-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4baf1-105">Return Value</span></span>  
  
|<span data-ttu-id="4baf1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4baf1-106">HRESULT</span></span>|<span data-ttu-id="4baf1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4baf1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4baf1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4baf1-108">S_OK</span></span>|<span data-ttu-id="4baf1-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4baf1-109">The operation was successful.</span></span>|  
|<span data-ttu-id="4baf1-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4baf1-110">S_FALSE</span></span>|<span data-ttu-id="4baf1-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="4baf1-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4baf1-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4baf1-112">E_FAIL</span></span>|<span data-ttu-id="4baf1-113">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="4baf1-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4baf1-114">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="4baf1-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4baf1-115">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4baf1-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4baf1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4baf1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4baf1-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4baf1-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4baf1-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4baf1-118">Remarks</span></span>  
 <span data-ttu-id="4baf1-119">Obvykle není nutné volat metodu `Stop`, protože kód se zastaví, když se proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="4baf1-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4baf1-120">Po volání `Stop`nelze modul CLR znovu inicializovat do stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="4baf1-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4baf1-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4baf1-121">Requirements</span></span>  
 <span data-ttu-id="4baf1-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4baf1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4baf1-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4baf1-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4baf1-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4baf1-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4baf1-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4baf1-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4baf1-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4baf1-126">See also</span></span>

- [<span data-ttu-id="4baf1-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4baf1-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
