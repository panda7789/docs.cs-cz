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
ms.openlocfilehash: d8cfb2f18bcceed3a125ac7876122c02d2267698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436452"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="918c4-102">ICLRReferenceAssemblyEnum::Get – metoda</span><span class="sxs-lookup"><span data-stu-id="918c4-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="918c4-103">Získá identitu sestavení v zadané hodnotě indexu.</span><span class="sxs-lookup"><span data-stu-id="918c4-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="918c4-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="918c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="918c4-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="918c4-106">[v] Index založený na nule identity sestavení vrátit.</span><span class="sxs-lookup"><span data-stu-id="918c4-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="918c4-107">[out] Vyrovnávací paměť obsahující data identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="918c4-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="918c4-108">[ve out] Velikost `pwzBuffer` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="918c4-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="918c4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="918c4-109">Return Value</span></span>  
  
|<span data-ttu-id="918c4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="918c4-110">HRESULT</span></span>|<span data-ttu-id="918c4-111">Popis</span><span class="sxs-lookup"><span data-stu-id="918c4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="918c4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="918c4-112">S_OK</span></span>|<span data-ttu-id="918c4-113">`Get` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="918c4-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="918c4-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="918c4-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="918c4-115">`pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="918c4-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="918c4-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="918c4-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="918c4-117">Výčet neobsahuje žádné další položky.</span><span class="sxs-lookup"><span data-stu-id="918c4-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="918c4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="918c4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="918c4-119">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="918c4-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="918c4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="918c4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="918c4-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="918c4-121">The call timed out.</span></span>|  
|<span data-ttu-id="918c4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="918c4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="918c4-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="918c4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="918c4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="918c4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="918c4-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="918c4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="918c4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="918c4-126">E_FAIL</span></span>|<span data-ttu-id="918c4-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="918c4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="918c4-128">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="918c4-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="918c4-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="918c4-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="918c4-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="918c4-130">Remarks</span></span>  
 <span data-ttu-id="918c4-131">`Get` obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="918c4-131">`Get` is typically called twice.</span></span> <span data-ttu-id="918c4-132">První volání poskytuje hodnotu null pro `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="918c4-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="918c4-133">Druhé volání poskytuje správně velikostí `pwzBuffer`a obsahuje identifikační údaje kanonický sestavení po dokončení.</span><span class="sxs-lookup"><span data-stu-id="918c4-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="918c4-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="918c4-134">Requirements</span></span>  
 <span data-ttu-id="918c4-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="918c4-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="918c4-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="918c4-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="918c4-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="918c4-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="918c4-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="918c4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="918c4-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="918c4-139">See Also</span></span>  
 [<span data-ttu-id="918c4-140">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="918c4-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="918c4-141">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="918c4-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
