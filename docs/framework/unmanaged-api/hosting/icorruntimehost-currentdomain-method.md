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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cb5ff5300a7fd2577e602b3077dd816cf7dfbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181377"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="8fcdb-102">ICorRuntimeHost::CurrentDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8fcdb-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="8fcdb-103">Získá ukazatel rozhraní typu <xref:System.AppDomain?displayProperty=nameWithType> , která představuje doménu načten v aktuálním vláknu.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fcdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fcdb-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fcdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fcdb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8fcdb-106">[out] Ukazatel typu <xref:System.AppDomain?displayProperty=nameWithType> , který představuje aktuální domény aplikace vlákna.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="8fcdb-107">Je zadán ukazatel this `IUnknown`, takže obecně by měly volat volající `QueryInterface` získat ukazatel typu <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fcdb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8fcdb-108">Return Value</span></span>  
  
|<span data-ttu-id="8fcdb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8fcdb-109">HRESULT</span></span>|<span data-ttu-id="8fcdb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8fcdb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8fcdb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8fcdb-111">S_OK</span></span>|<span data-ttu-id="8fcdb-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-112">The operation was successful.</span></span>|  
|<span data-ttu-id="8fcdb-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8fcdb-113">S_FALSE</span></span>|<span data-ttu-id="8fcdb-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8fcdb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8fcdb-115">E_FAIL</span></span>|<span data-ttu-id="8fcdb-116">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8fcdb-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8fcdb-118">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8fcdb-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8fcdb-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8fcdb-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8fcdb-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8fcdb-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fcdb-121">Requirements</span></span>  
 <span data-ttu-id="8fcdb-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fcdb-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fcdb-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fcdb-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fcdb-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fcdb-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fcdb-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8fcdb-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fcdb-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fcdb-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="8fcdb-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fcdb-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
