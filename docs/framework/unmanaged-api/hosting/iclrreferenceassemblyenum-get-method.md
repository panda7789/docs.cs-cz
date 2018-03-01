---
title: "ICLRReferenceAssemblyEnum::Get – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3cdf6a8eb761367d23e1ce61cd24727e7a3d6ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="ed31b-102">ICLRReferenceAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="ed31b-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="ed31b-103">Získá identitu sestavení v zadané hodnotě indexu.</span><span class="sxs-lookup"><span data-stu-id="ed31b-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed31b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed31b-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed31b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed31b-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="ed31b-106">[v] Index založený na nule identity sestavení vrátit.</span><span class="sxs-lookup"><span data-stu-id="ed31b-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="ed31b-107">[out] Vyrovnávací paměť obsahující data identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed31b-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="ed31b-108">[ve out] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ed31b-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed31b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed31b-109">Return Value</span></span>  
  
|<span data-ttu-id="ed31b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed31b-110">HRESULT</span></span>|<span data-ttu-id="ed31b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ed31b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed31b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed31b-112">S_OK</span></span>|<span data-ttu-id="ed31b-113">`Get`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ed31b-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="ed31b-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ed31b-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ed31b-115">`pwzBuffer`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="ed31b-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="ed31b-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="ed31b-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="ed31b-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="ed31b-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="ed31b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed31b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed31b-119">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ed31b-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed31b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed31b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed31b-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ed31b-121">The call timed out.</span></span>|  
|<span data-ttu-id="ed31b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed31b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed31b-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ed31b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed31b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed31b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed31b-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ed31b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed31b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed31b-126">E_FAIL</span></span>|<span data-ttu-id="ed31b-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ed31b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed31b-128">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ed31b-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed31b-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed31b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed31b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed31b-130">Remarks</span></span>  
 <span data-ttu-id="ed31b-131">`Get`obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="ed31b-131">`Get` is typically called twice.</span></span> <span data-ttu-id="ed31b-132">První volání poskytuje hodnotu null pro `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ed31b-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="ed31b-133">Druhé volání poskytuje správně velikostí `pwzBuffer`a obsahuje identifikační údaje kanonický sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="ed31b-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed31b-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed31b-134">Requirements</span></span>  
 <span data-ttu-id="ed31b-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed31b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed31b-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed31b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed31b-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed31b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed31b-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed31b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed31b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed31b-139">See Also</span></span>  
 [<span data-ttu-id="ed31b-140">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed31b-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ed31b-141">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed31b-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
