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
ms.openlocfilehash: ea66c142afc097d1003df4e7f5f5b960a91e2ab0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703382"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="a1186-102">ICLRProbingAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="a1186-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="a1186-103">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="a1186-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1186-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1186-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1186-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1186-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a1186-106">pro Index založený na nule identity sestavení, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="a1186-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a1186-107">mimo Vyrovnávací paměť obsahující data identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1186-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a1186-108">[in, out] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a1186-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1186-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a1186-109">Return Value</span></span>  
  
|<span data-ttu-id="a1186-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1186-110">HRESULT</span></span>|<span data-ttu-id="a1186-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a1186-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1186-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1186-112">S_OK</span></span>|<span data-ttu-id="a1186-113">`Get`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a1186-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="a1186-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a1186-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a1186-115">`pwzBuffer`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="a1186-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a1186-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="a1186-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="a1186-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="a1186-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="a1186-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1186-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1186-119">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a1186-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1186-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1186-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1186-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a1186-121">The call timed out.</span></span>|  
|<span data-ttu-id="a1186-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1186-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1186-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a1186-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1186-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1186-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1186-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a1186-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1186-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1186-126">E_FAIL</span></span>|<span data-ttu-id="a1186-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a1186-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1186-128">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a1186-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1186-129">Následná volání jakékoli metody hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1186-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1186-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1186-130">Remarks</span></span>  
 <span data-ttu-id="a1186-131">Identita na indexu 0 je identita specifická pro architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="a1186-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="a1186-132">Identita na indexu 1 je sestavení neutrální pro architekturu pro jazyk MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a1186-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a1186-133">Identita na indexu 2 neobsahuje žádné informace o architektuře.</span><span class="sxs-lookup"><span data-stu-id="a1186-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="a1186-134">`Get`se obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a1186-134">`Get` is typically called twice.</span></span> <span data-ttu-id="a1186-135">První volání dodá hodnotu null pro `pwzBuffer` a nastaví `pcchBufferSize` velikost vhodnou pro `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="a1186-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="a1186-136">Druhé volání dodá odpovídající velikost `pwzBuffer` a obsahuje kanonická data identity sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="a1186-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1186-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1186-137">Requirements</span></span>  
 <span data-ttu-id="a1186-138">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1186-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1186-139">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1186-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1186-140">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1186-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1186-141">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1186-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1186-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1186-142">See also</span></span>

- [<span data-ttu-id="a1186-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1186-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="a1186-144">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1186-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
