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
ms.openlocfilehash: 5afa7b37b804b6a11a894e0e6c7708c7787a20ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703361"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="00506-102">ICLRReferenceAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="00506-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="00506-103">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="00506-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00506-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00506-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00506-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="00506-106">pro Index založený na nule identity sestavení, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="00506-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="00506-107">mimo Vyrovnávací paměť obsahující data identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="00506-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="00506-108">[in, out] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="00506-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00506-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00506-109">Return Value</span></span>  
  
|<span data-ttu-id="00506-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00506-110">HRESULT</span></span>|<span data-ttu-id="00506-111">Popis</span><span class="sxs-lookup"><span data-stu-id="00506-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00506-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00506-112">S_OK</span></span>|<span data-ttu-id="00506-113">`Get`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="00506-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="00506-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="00506-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="00506-115">`pwzBuffer`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="00506-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="00506-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="00506-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="00506-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="00506-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="00506-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00506-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00506-119">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="00506-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00506-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00506-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00506-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="00506-121">The call timed out.</span></span>|  
|<span data-ttu-id="00506-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00506-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00506-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="00506-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00506-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00506-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00506-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="00506-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00506-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00506-126">E_FAIL</span></span>|<span data-ttu-id="00506-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="00506-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00506-128">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="00506-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00506-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="00506-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00506-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00506-130">Remarks</span></span>  
 <span data-ttu-id="00506-131">`Get`se obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="00506-131">`Get` is typically called twice.</span></span> <span data-ttu-id="00506-132">První volání dodá hodnotu null pro `pwzBuffer` a nastaví `pcchBufferSize` velikost vhodnou pro `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="00506-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="00506-133">Druhé volání dodá odpovídající velikost `pwzBuffer` a obsahuje kanonická data identity sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="00506-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00506-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00506-134">Requirements</span></span>  
 <span data-ttu-id="00506-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00506-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00506-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00506-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00506-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="00506-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00506-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00506-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00506-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="00506-139">See also</span></span>

- [<span data-ttu-id="00506-140">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00506-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="00506-141">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00506-141">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
