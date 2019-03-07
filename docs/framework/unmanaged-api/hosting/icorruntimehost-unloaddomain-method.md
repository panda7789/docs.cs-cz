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
ms.openlocfilehash: 6773d9387ae3b91125b413dee51b0c3fcbbb1edd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502017"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="c9a69-102">ICorRuntimeHost::UnloadDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c9a69-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="c9a69-103">Uvolní zadanou doménu aplikace z aktuálního procesu.</span><span class="sxs-lookup"><span data-stu-id="c9a69-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9a69-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9a69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9a69-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c9a69-106">[in] Ukazatel typu <xref:System._AppDomain?displayProperty=nameWithType> , která představuje doménu, kterou chcete uvolnit.</span><span class="sxs-lookup"><span data-stu-id="c9a69-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9a69-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9a69-107">Return Value</span></span>  
  
|<span data-ttu-id="c9a69-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9a69-108">HRESULT</span></span>|<span data-ttu-id="c9a69-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c9a69-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9a69-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9a69-110">S_OK</span></span>|<span data-ttu-id="c9a69-111">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c9a69-111">The operation was successful.</span></span>|  
|<span data-ttu-id="c9a69-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c9a69-112">S_FALSE</span></span>|<span data-ttu-id="c9a69-113">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="c9a69-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c9a69-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9a69-114">E_FAIL</span></span>|<span data-ttu-id="c9a69-115">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c9a69-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c9a69-116">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="c9a69-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c9a69-117">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9a69-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9a69-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9a69-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9a69-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c9a69-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9a69-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9a69-120">Requirements</span></span>  
 <span data-ttu-id="c9a69-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9a69-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a69-122">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9a69-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9a69-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9a69-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9a69-124">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c9a69-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a69-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a69-125">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="c9a69-126">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9a69-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
