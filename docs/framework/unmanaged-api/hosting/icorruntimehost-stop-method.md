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
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762692"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="52fb8-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="52fb8-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="52fb8-103">Zastaví provádění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="52fb8-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52fb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52fb8-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="52fb8-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52fb8-105">Return Value</span></span>  
  
|<span data-ttu-id="52fb8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52fb8-106">HRESULT</span></span>|<span data-ttu-id="52fb8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="52fb8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52fb8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="52fb8-108">S_OK</span></span>|<span data-ttu-id="52fb8-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="52fb8-109">The operation was successful.</span></span>|  
|<span data-ttu-id="52fb8-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="52fb8-110">S_FALSE</span></span>|<span data-ttu-id="52fb8-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="52fb8-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="52fb8-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52fb8-112">E_FAIL</span></span>|<span data-ttu-id="52fb8-113">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="52fb8-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="52fb8-114">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="52fb8-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="52fb8-115">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52fb8-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="52fb8-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52fb8-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52fb8-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="52fb8-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52fb8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52fb8-118">Remarks</span></span>  
 <span data-ttu-id="52fb8-119">Obvykle není nutné volat `Stop` metodu, protože kód se zastaví, když se proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="52fb8-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52fb8-120">Po volání do nástroje `Stop` nelze modul CLR znovu inicializovat do stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="52fb8-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52fb8-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52fb8-121">Requirements</span></span>  
 <span data-ttu-id="52fb8-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52fb8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52fb8-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52fb8-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52fb8-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52fb8-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52fb8-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="52fb8-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52fb8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="52fb8-126">See also</span></span>

- [<span data-ttu-id="52fb8-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52fb8-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
