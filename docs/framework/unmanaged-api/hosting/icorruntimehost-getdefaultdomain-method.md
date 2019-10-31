---
title: ICorRuntimeHost::GetDefaultDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139556"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="d5340-102">ICorRuntimeHost::GetDefaultDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d5340-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="d5340-103">Načte ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType>, který představuje výchozí doménu pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="d5340-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5340-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5340-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5340-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5340-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d5340-106">mimo Ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> do instance <xref:System.AppDomain>, která představuje výchozí doménu aplikace pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="d5340-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="d5340-107">Tento ukazatel je typu `IUnknown`, takže volající by obecně měli volat `QueryInterface`, aby získal ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d5340-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5340-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5340-108">Return Value</span></span>  
  
|<span data-ttu-id="d5340-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5340-109">HRESULT</span></span>|<span data-ttu-id="d5340-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d5340-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5340-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5340-111">S_OK</span></span>|<span data-ttu-id="d5340-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d5340-112">The operation was successful.</span></span>|  
|<span data-ttu-id="d5340-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d5340-113">S_FALSE</span></span>|<span data-ttu-id="d5340-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="d5340-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d5340-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5340-115">E_FAIL</span></span>|<span data-ttu-id="d5340-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="d5340-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d5340-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="d5340-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d5340-118">Následná volání všech hostitelských rozhraní API vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5340-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d5340-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5340-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5340-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d5340-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5340-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5340-121">Requirements</span></span>  
 <span data-ttu-id="d5340-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5340-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5340-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5340-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5340-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5340-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5340-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="d5340-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5340-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5340-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="d5340-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5340-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
