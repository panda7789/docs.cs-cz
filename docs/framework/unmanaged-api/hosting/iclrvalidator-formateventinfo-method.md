---
title: ICLRValidator::FormatEventInfo – metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 164a8c15a501af44aabb95852400621f05bbe873
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762780"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="723f0-102">ICLRValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="723f0-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="723f0-103">Získá podrobnou zprávu o zadané chybě ověřování.</span><span class="sxs-lookup"><span data-stu-id="723f0-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="723f0-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="723f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="723f0-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="723f0-106">pro Hodnota HRESULT, která byla předána obslužné rutině chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="723f0-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="723f0-107">pro `VEContext`Instance obsahující kontextové informace o chybách ověřování.</span><span class="sxs-lookup"><span data-stu-id="723f0-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="723f0-108">[in, out] Popisná chybová zpráva</span><span class="sxs-lookup"><span data-stu-id="723f0-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="723f0-109">pro Maximální délka chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="723f0-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="723f0-110">pro Bezpečné pole dalších parametrů, které se má ve zprávě použít.</span><span class="sxs-lookup"><span data-stu-id="723f0-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="723f0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="723f0-111">Return Value</span></span>  
  
|<span data-ttu-id="723f0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="723f0-112">HRESULT</span></span>|<span data-ttu-id="723f0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="723f0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="723f0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="723f0-114">S_OK</span></span>|<span data-ttu-id="723f0-115">`FormatEventInfo`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="723f0-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="723f0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="723f0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="723f0-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="723f0-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="723f0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="723f0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="723f0-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="723f0-119">The call timed out.</span></span>|  
|<span data-ttu-id="723f0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="723f0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="723f0-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="723f0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="723f0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="723f0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="723f0-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="723f0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="723f0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="723f0-124">E_FAIL</span></span>|<span data-ttu-id="723f0-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="723f0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="723f0-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="723f0-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="723f0-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="723f0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="723f0-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="723f0-128">Requirements</span></span>  
 <span data-ttu-id="723f0-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723f0-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723f0-130">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="723f0-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="723f0-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="723f0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="723f0-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723f0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723f0-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="723f0-133">See also</span></span>

- [<span data-ttu-id="723f0-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="723f0-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="723f0-135">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="723f0-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
