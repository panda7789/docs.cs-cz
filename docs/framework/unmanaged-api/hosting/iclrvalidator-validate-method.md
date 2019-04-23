---
title: ICLRValidator::Validate – metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 559c265c70c199e64782ba185d4925d293d6a778
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158688"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="100f2-102">ICLRValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="100f2-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="100f2-103">Ověří (PE portable executable) nebo Microsoft intermediate language (MSIL) do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="100f2-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="100f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="100f2-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
## <a name="parameters"></a><span data-ttu-id="100f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="100f2-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="100f2-106">[in] Ukazatel `IVEHandler` instanci, která zpracovává chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="100f2-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="100f2-107">[in] Identifikátor pro aktuální <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="100f2-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="100f2-108">[in] Kombinace [validatorflags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty určující druh ověřování, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="100f2-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="100f2-109">[in] Maximální počet chyb, aby před ukončením ověření.</span><span class="sxs-lookup"><span data-stu-id="100f2-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="100f2-110">[in] Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="100f2-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="100f2-111">[in] Název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="100f2-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="100f2-112">[in] Ukazatel do vyrovnávací paměti souboru.</span><span class="sxs-lookup"><span data-stu-id="100f2-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="100f2-113">[in] Velikost v bajtech, soubor, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="100f2-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="100f2-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="100f2-114">Return Value</span></span>  
  
|<span data-ttu-id="100f2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="100f2-115">HRESULT</span></span>|<span data-ttu-id="100f2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="100f2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="100f2-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="100f2-117">S_OK</span></span>|<span data-ttu-id="100f2-118">`Validate` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="100f2-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="100f2-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="100f2-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="100f2-120">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="100f2-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="100f2-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="100f2-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="100f2-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="100f2-122">The call timed out.</span></span>|  
|<span data-ttu-id="100f2-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="100f2-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="100f2-124">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="100f2-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="100f2-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="100f2-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="100f2-126">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="100f2-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="100f2-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="100f2-127">E_FAIL</span></span>|<span data-ttu-id="100f2-128">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="100f2-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="100f2-129">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="100f2-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="100f2-130">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="100f2-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="100f2-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="100f2-131">Requirements</span></span>  
 <span data-ttu-id="100f2-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="100f2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="100f2-133">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="100f2-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="100f2-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="100f2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="100f2-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="100f2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100f2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="100f2-136">See also</span></span>

- [<span data-ttu-id="100f2-137">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="100f2-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
