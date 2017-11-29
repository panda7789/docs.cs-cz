---
title: "ICorRuntimeHost::Start – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f259a28009ed12583bc8f7baa63e2ca17e4a21e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="9b71c-102">ICorRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="9b71c-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="9b71c-103">Spustí modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="9b71c-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b71c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b71c-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9b71c-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b71c-105">Return Value</span></span>  
  
|<span data-ttu-id="9b71c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b71c-106">HRESULT</span></span>|<span data-ttu-id="9b71c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9b71c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b71c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b71c-108">S_OK</span></span>|<span data-ttu-id="9b71c-109">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9b71c-109">The operation was successful.</span></span>|  
|<span data-ttu-id="9b71c-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9b71c-110">S_FALSE</span></span>|<span data-ttu-id="9b71c-111">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="9b71c-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9b71c-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b71c-112">E_FAIL</span></span>|<span data-ttu-id="9b71c-113">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="9b71c-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9b71c-114">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="9b71c-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="9b71c-115">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b71c-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b71c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b71c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b71c-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9b71c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b71c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b71c-118">Remarks</span></span>  
 <span data-ttu-id="9b71c-119">Obvykle není nutné volat `Start` metoda, protože modul CLR spustí automaticky po první požadavek na spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9b71c-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b71c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b71c-120">Requirements</span></span>  
 <span data-ttu-id="9b71c-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b71c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b71c-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b71c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b71c-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b71c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b71c-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9b71c-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b71c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b71c-125">See Also</span></span>  
 [<span data-ttu-id="9b71c-126">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b71c-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
