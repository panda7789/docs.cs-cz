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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7354536db483ad93d29fef29745af44a6f90884c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779922"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="cee73-102">ICLRValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cee73-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="cee73-103">Získá podrobnou zprávu o chybě ověření pro zadané.</span><span class="sxs-lookup"><span data-stu-id="cee73-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cee73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cee73-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cee73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cee73-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="cee73-106">[in] Hodnota HRESULT, který byl předán obslužná rutina chyb ověření.</span><span class="sxs-lookup"><span data-stu-id="cee73-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="cee73-107">[in] A `VEContext` instance, která obsahuje kontextové informace o chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="cee73-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="cee73-108">[out v] Popisná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cee73-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="cee73-109">[in] Maximální délka chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cee73-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="cee73-110">[in] Bezpečné pole další parametry, který se má použít ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="cee73-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cee73-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cee73-111">Return Value</span></span>  
  
|<span data-ttu-id="cee73-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cee73-112">HRESULT</span></span>|<span data-ttu-id="cee73-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cee73-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cee73-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cee73-114">S_OK</span></span>|<span data-ttu-id="cee73-115">`FormatEventInfo` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="cee73-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="cee73-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cee73-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cee73-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cee73-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cee73-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cee73-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cee73-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cee73-119">The call timed out.</span></span>|  
|<span data-ttu-id="cee73-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cee73-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cee73-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="cee73-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cee73-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cee73-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cee73-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="cee73-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cee73-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cee73-124">E_FAIL</span></span>|<span data-ttu-id="cee73-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="cee73-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cee73-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cee73-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cee73-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cee73-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cee73-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cee73-128">Requirements</span></span>  
 <span data-ttu-id="cee73-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cee73-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cee73-130">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="cee73-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="cee73-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cee73-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cee73-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cee73-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee73-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cee73-133">See also</span></span>

- [<span data-ttu-id="cee73-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cee73-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="cee73-135">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cee73-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
