---
title: "ICorRuntimeHost::CurrentDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CurrentDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 592b604f5e873f479f2e0489144240c3f021c270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="793bf-102">ICorRuntimeHost::CurrentDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="793bf-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="793bf-103">Získá ukazatele rozhraní typu <xref:System.AppDomain?displayProperty=nameWithType> představující domény načtené na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="793bf-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="793bf-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="793bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="793bf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="793bf-106">[out] Ukazatel typu <xref:System.AppDomain?displayProperty=nameWithType> představující aktuální doménu aplikace vlákna.</span><span class="sxs-lookup"><span data-stu-id="793bf-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="793bf-107">Tento ukazatel je zadán `IUnknown`, takže volající by měly volat obecně `QueryInterface` získat ukazatel typu <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="793bf-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="793bf-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="793bf-108">Return Value</span></span>  
  
|<span data-ttu-id="793bf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="793bf-109">HRESULT</span></span>|<span data-ttu-id="793bf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="793bf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="793bf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="793bf-111">S_OK</span></span>|<span data-ttu-id="793bf-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="793bf-112">The operation was successful.</span></span>|  
|<span data-ttu-id="793bf-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="793bf-113">S_FALSE</span></span>|<span data-ttu-id="793bf-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="793bf-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="793bf-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="793bf-115">E_FAIL</span></span>|<span data-ttu-id="793bf-116">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="793bf-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="793bf-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="793bf-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="793bf-118">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="793bf-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="793bf-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="793bf-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="793bf-120">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="793bf-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="793bf-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="793bf-121">Requirements</span></span>  
 <span data-ttu-id="793bf-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="793bf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="793bf-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="793bf-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="793bf-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="793bf-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="793bf-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="793bf-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793bf-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="793bf-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="793bf-127">Icorruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="793bf-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
