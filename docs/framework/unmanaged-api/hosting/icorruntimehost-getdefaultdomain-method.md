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
ms.openlocfilehash: 41a6c5ee73cad77368e83792d11d455d8fb163fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937025"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="686b3-102">ICorRuntimeHost::GetDefaultDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="686b3-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="686b3-103">Získá ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> , která představuje výchozí doménu pro aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="686b3-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="686b3-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="686b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="686b3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="686b3-106">[out] Ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType> k <xref:System.AppDomain> instanci, která představuje výchozí domény aplikace pro proces.</span><span class="sxs-lookup"><span data-stu-id="686b3-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="686b3-107">Je zadán ukazatel this `IUnknown`, takže obecně by měly volat volající `QueryInterface` získat ukazatel rozhraní typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="686b3-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="686b3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="686b3-108">Return Value</span></span>  
  
|<span data-ttu-id="686b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="686b3-109">HRESULT</span></span>|<span data-ttu-id="686b3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="686b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="686b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="686b3-111">S_OK</span></span>|<span data-ttu-id="686b3-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="686b3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="686b3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="686b3-113">S_FALSE</span></span>|<span data-ttu-id="686b3-114">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="686b3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="686b3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="686b3-115">E_FAIL</span></span>|<span data-ttu-id="686b3-116">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="686b3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="686b3-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="686b3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="686b3-118">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="686b3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="686b3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="686b3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="686b3-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="686b3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="686b3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="686b3-121">Requirements</span></span>  
 <span data-ttu-id="686b3-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="686b3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686b3-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="686b3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="686b3-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="686b3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="686b3-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="686b3-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686b3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="686b3-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="686b3-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="686b3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
