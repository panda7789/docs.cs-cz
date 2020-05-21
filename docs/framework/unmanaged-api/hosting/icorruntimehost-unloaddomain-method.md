---
title: ICorRuntimeHost::UnloadDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: 558b6e4c6ac369e33be3d45b7241e8b11db8bfae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760391"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="40e6f-102">ICorRuntimeHost::UnloadDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="40e6f-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="40e6f-103">Uvolní zadanou doménu aplikace z aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="40e6f-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40e6f-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40e6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40e6f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="40e6f-106">pro Ukazatel typu <xref:System._AppDomain?displayProperty=nameWithType> , který představuje doménu, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="40e6f-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40e6f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40e6f-107">Return Value</span></span>  
  
|<span data-ttu-id="40e6f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40e6f-108">HRESULT</span></span>|<span data-ttu-id="40e6f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="40e6f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40e6f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="40e6f-110">S_OK</span></span>|<span data-ttu-id="40e6f-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="40e6f-111">The operation was successful.</span></span>|  
|<span data-ttu-id="40e6f-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="40e6f-112">S_FALSE</span></span>|<span data-ttu-id="40e6f-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="40e6f-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="40e6f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40e6f-114">E_FAIL</span></span>|<span data-ttu-id="40e6f-115">Došlo k neznámému a závažnému selhání.</span><span class="sxs-lookup"><span data-stu-id="40e6f-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="40e6f-116">Pokud metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v procesu použit.</span><span class="sxs-lookup"><span data-stu-id="40e6f-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="40e6f-117">Následná volání všech hostitelských rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="40e6f-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="40e6f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40e6f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40e6f-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="40e6f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40e6f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40e6f-120">Requirements</span></span>  
 <span data-ttu-id="40e6f-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e6f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e6f-122">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40e6f-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40e6f-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40e6f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40e6f-124">**Verze .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="40e6f-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e6f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="40e6f-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="40e6f-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40e6f-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
