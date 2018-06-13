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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4db96133315b23a2d0b4bd32b597ee03f5d697b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438113"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="c5104-102">ICorRuntimeHost::UnloadDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c5104-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="c5104-103">Uvolní doménu zadané aplikace z aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c5104-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5104-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5104-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5104-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5104-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c5104-106">[v] Ukazatel typu <xref:System._AppDomain?displayProperty=nameWithType> představující domény, aby jej odpojit.</span><span class="sxs-lookup"><span data-stu-id="c5104-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5104-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c5104-107">Return Value</span></span>  
  
|<span data-ttu-id="c5104-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5104-108">HRESULT</span></span>|<span data-ttu-id="c5104-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c5104-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5104-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5104-110">S_OK</span></span>|<span data-ttu-id="c5104-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c5104-111">The operation was successful.</span></span>|  
|<span data-ttu-id="c5104-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c5104-112">S_FALSE</span></span>|<span data-ttu-id="c5104-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="c5104-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c5104-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5104-114">E_FAIL</span></span>|<span data-ttu-id="c5104-115">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="c5104-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c5104-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="c5104-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c5104-117">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5104-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c5104-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5104-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5104-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c5104-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5104-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5104-120">Requirements</span></span>  
 <span data-ttu-id="c5104-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5104-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5104-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5104-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5104-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5104-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5104-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c5104-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5104-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5104-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="c5104-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5104-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
