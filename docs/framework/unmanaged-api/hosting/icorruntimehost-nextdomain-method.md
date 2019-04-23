---
title: ICorRuntimeHost::NextDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c3ff0c91713a6bb7449791bae6a754c43659335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225271"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="d9ee8-102">ICorRuntimeHost::NextDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="d9ee8-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="d9ee8-103">Získá ukazatel rozhraní na další doménu ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ee8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9ee8-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ee8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9ee8-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d9ee8-106">[in] Enumerátor, který byl získán pomocí volání [enumdomains –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="d9ee8-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="d9ee8-107">[out] Ukazatel rozhraní k <xref:System._AppDomain?displayProperty=nameWithType> typ, který představuje další domény ve výčtu nebo hodnota null, pokud neexistuje žádné další domény.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9ee8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9ee8-108">Return Value</span></span>  
  
|<span data-ttu-id="d9ee8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9ee8-109">HRESULT</span></span>|<span data-ttu-id="d9ee8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d9ee8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9ee8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9ee8-111">S_OK</span></span>|<span data-ttu-id="d9ee8-112">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-112">The operation was successful.</span></span>|  
|<span data-ttu-id="d9ee8-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d9ee8-113">S_FALSE</span></span>|<span data-ttu-id="d9ee8-114">Nepodařilo se dokončit operaci, nebo neexistují žádné další domény ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="d9ee8-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9ee8-115">E_FAIL</span></span>|<span data-ttu-id="d9ee8-116">Došlo k neznámé, katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d9ee8-117">Pokud metoda vrátí E_FAIL, modul CLR (CLR) už nejsou použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d9ee8-118">Následující volání jakékoli hostitelské rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9ee8-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9ee8-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9ee8-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d9ee8-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9ee8-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9ee8-121">Requirements</span></span>  
 <span data-ttu-id="d9ee8-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ee8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ee8-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9ee8-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9ee8-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9ee8-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9ee8-125">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d9ee8-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ee8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9ee8-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="d9ee8-127">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9ee8-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
