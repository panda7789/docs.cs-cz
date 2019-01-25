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
ms.openlocfilehash: 31b99ce4435c1282380291e3c3c15723381e8ab4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741844"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="db629-102">ICLRValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="db629-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="db629-103">Získá podrobnou zprávu o chybě ověření pro zadané.</span><span class="sxs-lookup"><span data-stu-id="db629-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db629-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db629-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db629-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db629-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="db629-106">[in] Hodnota HRESULT, který byl předán obslužná rutina chyb ověření.</span><span class="sxs-lookup"><span data-stu-id="db629-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="db629-107">[in] A `VEContext` instance, která obsahuje kontextové informace o chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="db629-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="db629-108">[out v] Popisná chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="db629-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="db629-109">[in] Maximální délka chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="db629-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="db629-110">[in] Bezpečné pole další parametry, který se má použít ve zprávě.</span><span class="sxs-lookup"><span data-stu-id="db629-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db629-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db629-111">Return Value</span></span>  
  
|<span data-ttu-id="db629-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db629-112">HRESULT</span></span>|<span data-ttu-id="db629-113">Popis</span><span class="sxs-lookup"><span data-stu-id="db629-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db629-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="db629-114">S_OK</span></span>|<span data-ttu-id="db629-115">`FormatEventInfo` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="db629-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="db629-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db629-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db629-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="db629-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db629-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db629-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db629-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="db629-119">The call timed out.</span></span>|  
|<span data-ttu-id="db629-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db629-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db629-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="db629-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db629-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db629-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db629-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="db629-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db629-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db629-124">E_FAIL</span></span>|<span data-ttu-id="db629-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="db629-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db629-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="db629-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db629-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db629-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db629-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db629-128">Requirements</span></span>  
 <span data-ttu-id="db629-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db629-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db629-130">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="db629-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="db629-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db629-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db629-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db629-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db629-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db629-133">See also</span></span>
- [<span data-ttu-id="db629-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db629-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="db629-135">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db629-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
