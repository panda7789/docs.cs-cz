---
title: ICLRProbingAssemblyEnum::Get – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 2ff1f9428a92d091a51a4cca12d69d98da0ecba2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120537"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="6a2da-102">ICLRProbingAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="6a2da-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="6a2da-103">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="6a2da-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a2da-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a2da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a2da-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="6a2da-106">pro Index založený na nule identity sestavení, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="6a2da-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6a2da-107">mimo Vyrovnávací paměť obsahující data identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="6a2da-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6a2da-108">[in, out] Velikost vyrovnávací paměti `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6a2da-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a2da-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a2da-109">Return Value</span></span>  
  
|<span data-ttu-id="6a2da-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a2da-110">HRESULT</span></span>|<span data-ttu-id="6a2da-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6a2da-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a2da-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a2da-112">S_OK</span></span>|<span data-ttu-id="6a2da-113">`Get` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6a2da-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="6a2da-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6a2da-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6a2da-115">`pwzBuffer` je příliš malý.</span><span class="sxs-lookup"><span data-stu-id="6a2da-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6a2da-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="6a2da-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="6a2da-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="6a2da-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="6a2da-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a2da-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a2da-119">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6a2da-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a2da-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a2da-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a2da-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6a2da-121">The call timed out.</span></span>|  
|<span data-ttu-id="6a2da-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a2da-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a2da-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6a2da-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a2da-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a2da-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a2da-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6a2da-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a2da-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a2da-126">E_FAIL</span></span>|<span data-ttu-id="6a2da-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6a2da-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a2da-128">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6a2da-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a2da-129">Následná volání jakékoli metody hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6a2da-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a2da-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a2da-130">Remarks</span></span>  
 <span data-ttu-id="6a2da-131">Identita na indexu 0 je identita specifická pro architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="6a2da-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="6a2da-132">Identita na indexu 1 je sestavení neutrální pro architekturu pro jazyk MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="6a2da-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="6a2da-133">Identita na indexu 2 neobsahuje žádné informace o architektuře.</span><span class="sxs-lookup"><span data-stu-id="6a2da-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="6a2da-134">`Get` se obvykle volá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="6a2da-134">`Get` is typically called twice.</span></span> <span data-ttu-id="6a2da-135">První volání dodá hodnotu null pro `pwzBuffer`a nastaví `pcchBufferSize` na velikost vhodnou pro `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="6a2da-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="6a2da-136">Druhé volání dodá vhodně velikost `pwzBuffer`a obsahuje kanonická data identity sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="6a2da-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a2da-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a2da-137">Requirements</span></span>  
 <span data-ttu-id="6a2da-138">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a2da-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a2da-139">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a2da-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a2da-140">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6a2da-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a2da-141">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a2da-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2da-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a2da-142">See also</span></span>

- [<span data-ttu-id="6a2da-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a2da-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="6a2da-144">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a2da-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
