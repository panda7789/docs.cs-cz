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
ms.openlocfilehash: 38042876cf4397418d2e6e6ed2bfbeb2df2d62d8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762289"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="b8f56-102">ICorRuntimeHost::CurrentDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="b8f56-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="b8f56-103">Načte ukazatel rozhraní typu <xref:System.AppDomain?displayProperty=nameWithType> , který představuje doménu načtenou v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="b8f56-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8f56-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8f56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8f56-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b8f56-106">mimo Ukazatel typu <xref:System.AppDomain?displayProperty=nameWithType> , který představuje aktuální doménu aplikace vlákna.</span><span class="sxs-lookup"><span data-stu-id="b8f56-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="b8f56-107">Tento ukazatel je zapsán `IUnknown` , takže volající by obecně volali `QueryInterface` k získání ukazatele typu <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="b8f56-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8f56-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8f56-108">Return Value</span></span>  
  
|<span data-ttu-id="b8f56-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8f56-109">HRESULT</span></span>|<span data-ttu-id="b8f56-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b8f56-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8f56-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8f56-111">S_OK</span></span>|<span data-ttu-id="b8f56-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b8f56-112">The operation was successful.</span></span>|  
|<span data-ttu-id="b8f56-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b8f56-113">S_FALSE</span></span>|<span data-ttu-id="b8f56-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="b8f56-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b8f56-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8f56-115">E_FAIL</span></span>|<span data-ttu-id="b8f56-116">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="b8f56-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b8f56-117">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="b8f56-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b8f56-118">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b8f56-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b8f56-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8f56-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8f56-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b8f56-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8f56-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8f56-121">Requirements</span></span>  
 <span data-ttu-id="b8f56-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f56-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f56-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b8f56-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8f56-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8f56-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8f56-125">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="b8f56-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f56-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8f56-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="b8f56-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8f56-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
