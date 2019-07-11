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
ms.openlocfilehash: a69e32d418478071f9b99a391e6bef9095d6f4ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749919"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="22d8c-102">ICLRReferenceAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="22d8c-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="22d8c-103">Získá identitu sestavení u zadaného indexu.</span><span class="sxs-lookup"><span data-stu-id="22d8c-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d8c-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22d8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d8c-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="22d8c-106">[in] Index založený na nule Identita sestavení vrátit.</span><span class="sxs-lookup"><span data-stu-id="22d8c-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="22d8c-107">[out] Vyrovnávací paměť obsahující data identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="22d8c-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="22d8c-108">[out v] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="22d8c-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22d8c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22d8c-109">Return Value</span></span>  
  
|<span data-ttu-id="22d8c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22d8c-110">HRESULT</span></span>|<span data-ttu-id="22d8c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="22d8c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22d8c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="22d8c-112">S_OK</span></span>|<span data-ttu-id="22d8c-113">`Get` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="22d8c-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="22d8c-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="22d8c-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="22d8c-115">`pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="22d8c-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="22d8c-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="22d8c-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="22d8c-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="22d8c-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="22d8c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22d8c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22d8c-119">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="22d8c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22d8c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22d8c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22d8c-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="22d8c-121">The call timed out.</span></span>|  
|<span data-ttu-id="22d8c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22d8c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22d8c-123">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="22d8c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22d8c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22d8c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22d8c-125">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="22d8c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22d8c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22d8c-126">E_FAIL</span></span>|<span data-ttu-id="22d8c-127">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="22d8c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22d8c-128">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="22d8c-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22d8c-129">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="22d8c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d8c-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22d8c-130">Remarks</span></span>  
 <span data-ttu-id="22d8c-131">`Get` je obvykle volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="22d8c-131">`Get` is typically called twice.</span></span> <span data-ttu-id="22d8c-132">První volání je zadán pro hodnotu null `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="22d8c-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="22d8c-133">Druhém volání je zadán odpovídající velikosti `pwzBuffer`a obsahuje data identit canonical sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="22d8c-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d8c-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d8c-134">Requirements</span></span>  
 <span data-ttu-id="22d8c-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d8c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d8c-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22d8c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22d8c-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22d8c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d8c-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d8c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d8c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d8c-139">See also</span></span>

- [<span data-ttu-id="22d8c-140">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d8c-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="22d8c-141">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d8c-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
