---
title: "ICLRProbingAssemblyEnum::Get – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd54558eeb49ebf7a2a2e9304830b09a08d1038e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="9d4f4-102">ICLRProbingAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="9d4f4-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="9d4f4-103">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4f4-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d4f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d4f4-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="9d4f4-106">[v] Index založený na nule identity sestavení vrátit.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9d4f4-107">[out] Vyrovnávací paměť obsahující data identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="9d4f4-108">[ve out] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d4f4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d4f4-109">Return Value</span></span>  
  
|<span data-ttu-id="9d4f4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d4f4-110">HRESULT</span></span>|<span data-ttu-id="9d4f4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9d4f4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d4f4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d4f4-112">S_OK</span></span>|<span data-ttu-id="9d4f4-113">`Get`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="9d4f4-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9d4f4-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9d4f4-115">`pwzBuffer`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="9d4f4-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="9d4f4-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="9d4f4-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="9d4f4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d4f4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d4f4-119">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d4f4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d4f4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d4f4-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-121">The call timed out.</span></span>|  
|<span data-ttu-id="9d4f4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d4f4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d4f4-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d4f4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d4f4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d4f4-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d4f4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d4f4-126">E_FAIL</span></span>|<span data-ttu-id="9d4f4-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d4f4-128">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d4f4-129">Následující volání žádné hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d4f4-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d4f4-130">Remarks</span></span>  
 <span data-ttu-id="9d4f4-131">Identita indexem 0 je identity, které jsou specifické pro architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="9d4f4-132">Identita indexem 1 je architektura jazykově neutrální sestavení pro Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="9d4f4-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="9d4f4-133">Identity na pozici 2 neobsahuje informace o architektuře.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="9d4f4-134">`Get`obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-134">`Get` is typically called twice.</span></span> <span data-ttu-id="9d4f4-135">První volání poskytuje hodnotu null pro `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="9d4f4-136">Druhé volání poskytuje správně velikostí `pwzBuffer`a obsahuje identifikační údaje kanonický sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="9d4f4-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4f4-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d4f4-137">Requirements</span></span>  
 <span data-ttu-id="9d4f4-138">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4f4-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4f4-139">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d4f4-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d4f4-140">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d4f4-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d4f4-141">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4f4-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4f4-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d4f4-142">See Also</span></span>  
 [<span data-ttu-id="9d4f4-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d4f4-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="9d4f4-144">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d4f4-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
