---
title: ICorRuntimeHost::CurrentDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: f2249d10159b1ff0be7ead0783efb8a2742d26b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139603"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="eba39-102">ICorRuntimeHost::CurrentDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="eba39-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="eba39-103">Načte ukazatel rozhraní typu <xref:System.AppDomain?displayProperty=nameWithType>, který představuje doménu načtenou v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="eba39-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba39-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eba39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eba39-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="eba39-106">mimo Ukazatel typu <xref:System.AppDomain?displayProperty=nameWithType>, který představuje aktuální doménu aplikace vlákna.</span><span class="sxs-lookup"><span data-stu-id="eba39-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="eba39-107">Tento ukazatel je typu `IUnknown`, takže volající by obecně měli volat `QueryInterface` a získat tak ukazatel typu <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="eba39-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eba39-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eba39-108">Return Value</span></span>  
  
|<span data-ttu-id="eba39-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eba39-109">HRESULT</span></span>|<span data-ttu-id="eba39-110">Popis</span><span class="sxs-lookup"><span data-stu-id="eba39-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eba39-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eba39-111">S_OK</span></span>|<span data-ttu-id="eba39-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="eba39-112">The operation was successful.</span></span>|  
|<span data-ttu-id="eba39-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="eba39-113">S_FALSE</span></span>|<span data-ttu-id="eba39-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="eba39-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="eba39-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eba39-115">E_FAIL</span></span>|<span data-ttu-id="eba39-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="eba39-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="eba39-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="eba39-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="eba39-118">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eba39-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eba39-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eba39-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eba39-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="eba39-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eba39-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eba39-121">Requirements</span></span>  
 <span data-ttu-id="eba39-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba39-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba39-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eba39-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eba39-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eba39-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eba39-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="eba39-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba39-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eba39-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="eba39-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eba39-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
