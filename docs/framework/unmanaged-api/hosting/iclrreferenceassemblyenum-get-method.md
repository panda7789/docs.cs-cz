---
title: ICLRReferenceAssemblyEnum::Get – metoda
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d26ed6249bad8a7e2fbaab01264c1b32e1ff55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194471"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="c345f-102">ICLRReferenceAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="c345f-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="c345f-103">Získá identitu sestavení u zadaného indexu.</span><span class="sxs-lookup"><span data-stu-id="c345f-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c345f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c345f-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c345f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c345f-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="c345f-106">[in] Index založený na nule Identita sestavení vrátit.</span><span class="sxs-lookup"><span data-stu-id="c345f-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="c345f-107">[out] Vyrovnávací paměť obsahující data identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="c345f-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="c345f-108">[out v] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c345f-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c345f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c345f-109">Return Value</span></span>  
  
|<span data-ttu-id="c345f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c345f-110">HRESULT</span></span>|<span data-ttu-id="c345f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c345f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c345f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c345f-112">S_OK</span></span>|<span data-ttu-id="c345f-113">`Get` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c345f-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="c345f-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c345f-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c345f-115">`pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="c345f-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="c345f-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="c345f-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="c345f-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="c345f-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="c345f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c345f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c345f-119">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c345f-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c345f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c345f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c345f-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c345f-121">The call timed out.</span></span>|  
|<span data-ttu-id="c345f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c345f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c345f-123">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c345f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c345f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c345f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c345f-125">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c345f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c345f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c345f-126">E_FAIL</span></span>|<span data-ttu-id="c345f-127">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c345f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c345f-128">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c345f-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c345f-129">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c345f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c345f-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c345f-130">Remarks</span></span>  
 <span data-ttu-id="c345f-131">`Get` je obvykle volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="c345f-131">`Get` is typically called twice.</span></span> <span data-ttu-id="c345f-132">První volání je zadán pro hodnotu null `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="c345f-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="c345f-133">Druhém volání je zadán odpovídající velikosti `pwzBuffer`a obsahuje data identit canonical sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="c345f-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c345f-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c345f-134">Requirements</span></span>  
 <span data-ttu-id="c345f-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c345f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c345f-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c345f-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c345f-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c345f-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c345f-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c345f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c345f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c345f-139">See also</span></span>

- [<span data-ttu-id="c345f-140">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c345f-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c345f-141">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c345f-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
