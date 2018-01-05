---
title: "ICorRuntimeHost::Stop – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9e27bd5d05b10f8db24a1119e4ed3717ce044e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="4f2cd-102">ICorRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="4f2cd-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="4f2cd-103">Zastaví spuštění kódu v modulu runtime pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f2cd-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4f2cd-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4f2cd-105">Return Value</span></span>  
  
|<span data-ttu-id="4f2cd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f2cd-106">HRESULT</span></span>|<span data-ttu-id="4f2cd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4f2cd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f2cd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f2cd-108">S_OK</span></span>|<span data-ttu-id="4f2cd-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-109">The operation was successful.</span></span>|  
|<span data-ttu-id="4f2cd-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4f2cd-110">S_FALSE</span></span>|<span data-ttu-id="4f2cd-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4f2cd-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f2cd-112">E_FAIL</span></span>|<span data-ttu-id="4f2cd-113">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4f2cd-114">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4f2cd-115">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4f2cd-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f2cd-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f2cd-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f2cd-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f2cd-118">Remarks</span></span>  
 <span data-ttu-id="4f2cd-119">Není obvykle nutné volat `Stop` metoda, protože kód zastaví provádění při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f2cd-120">Po volání `Stop`, modul CLR nelze znovu inicializovat do stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="4f2cd-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f2cd-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f2cd-121">Requirements</span></span>  
 <span data-ttu-id="4f2cd-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f2cd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f2cd-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f2cd-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f2cd-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f2cd-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f2cd-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="4f2cd-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2cd-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f2cd-126">See Also</span></span>  
 [<span data-ttu-id="4f2cd-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f2cd-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
