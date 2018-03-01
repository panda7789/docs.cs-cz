---
title: "ICLRValidator::FormatEventInfo – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4178d92bea44be269df8a69a628b6cb1a53dae4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="62cf3-102">ICLRValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="62cf3-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="62cf3-103">Získá podrobná zpráva o chybě zadaný ověření.</span><span class="sxs-lookup"><span data-stu-id="62cf3-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62cf3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62cf3-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62cf3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62cf3-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="62cf3-106">[v] Hodnota HRESULT, který byl předán na obslužnou rutinu chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="62cf3-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="62cf3-107">[v] A `VEContext` instanci, která obsahuje kontextové informace o chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="62cf3-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="62cf3-108">[ve out] Popisný chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="62cf3-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="62cf3-109">[v] Maximální délka chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="62cf3-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="62cf3-110">[v] Bezpečným polím další parametry, které budou použity ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="62cf3-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62cf3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62cf3-111">Return Value</span></span>  
  
|<span data-ttu-id="62cf3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62cf3-112">HRESULT</span></span>|<span data-ttu-id="62cf3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="62cf3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62cf3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="62cf3-114">S_OK</span></span>|<span data-ttu-id="62cf3-115">`FormatEventInfo`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="62cf3-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="62cf3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62cf3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62cf3-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="62cf3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62cf3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62cf3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62cf3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="62cf3-119">The call timed out.</span></span>|  
|<span data-ttu-id="62cf3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62cf3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62cf3-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="62cf3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62cf3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62cf3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62cf3-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="62cf3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62cf3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62cf3-124">E_FAIL</span></span>|<span data-ttu-id="62cf3-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="62cf3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62cf3-126">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="62cf3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62cf3-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="62cf3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62cf3-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62cf3-128">Requirements</span></span>  
 <span data-ttu-id="62cf3-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62cf3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62cf3-130">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="62cf3-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="62cf3-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62cf3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62cf3-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62cf3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62cf3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="62cf3-133">See Also</span></span>  
 [<span data-ttu-id="62cf3-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62cf3-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="62cf3-135">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62cf3-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
