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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe80050d7b513bce2660b81c5e4faa35b375f22b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780034"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="0fec7-102">ICorRuntimeHost::GetDefaultDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0fec7-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="0fec7-103">Získá ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> , která představuje výchozí doménu pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="0fec7-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fec7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fec7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fec7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fec7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0fec7-106">[out] Ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> k <xref:System.AppDomain> instanci, která představuje výchozí domény aplikace pro proces.</span><span class="sxs-lookup"><span data-stu-id="0fec7-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="0fec7-107">Je zadán ukazatel this `IUnknown`, takže obecně by měly volat volající `QueryInterface` získat ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fec7-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fec7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0fec7-108">Return Value</span></span>  
  
|<span data-ttu-id="0fec7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fec7-109">HRESULT</span></span>|<span data-ttu-id="0fec7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0fec7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fec7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0fec7-111">S_OK</span></span>|<span data-ttu-id="0fec7-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0fec7-112">The operation was successful.</span></span>|  
|<span data-ttu-id="0fec7-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0fec7-113">S_FALSE</span></span>|<span data-ttu-id="0fec7-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="0fec7-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0fec7-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0fec7-115">E_FAIL</span></span>|<span data-ttu-id="0fec7-116">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0fec7-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0fec7-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="0fec7-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0fec7-118">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0fec7-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0fec7-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0fec7-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0fec7-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0fec7-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fec7-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fec7-121">Requirements</span></span>  
 <span data-ttu-id="0fec7-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fec7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fec7-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0fec7-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fec7-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fec7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fec7-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0fec7-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fec7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fec7-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0fec7-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fec7-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
