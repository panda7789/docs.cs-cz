---
title: "ICLRValidator::Validate – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7328fe62276de6c33464ab8cfc6d6a5f39ee710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="afa61-102">ICLRValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="afa61-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="afa61-103">Ověří přenosné spustitelný soubor (PE) nebo Microsoft (MSIL intermediate language) do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="afa61-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afa61-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="afa61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afa61-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="afa61-106">[v] Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="afa61-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="afa61-107">[v] Identifikátor pro aktuální <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="afa61-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="afa61-108">[v] Kombinace [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty, která určuje druh ověřování, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="afa61-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="afa61-109">[v] Maximální počet chyb umožňující před ukončením ověření.</span><span class="sxs-lookup"><span data-stu-id="afa61-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="afa61-110">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="afa61-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="afa61-111">[v] Název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="afa61-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="afa61-112">[v] Ukazatel do vyrovnávací paměti souboru.</span><span class="sxs-lookup"><span data-stu-id="afa61-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="afa61-113">[v] Velikost v bajtech, soubor, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="afa61-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afa61-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="afa61-114">Return Value</span></span>  
  
|<span data-ttu-id="afa61-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afa61-115">HRESULT</span></span>|<span data-ttu-id="afa61-116">Popis</span><span class="sxs-lookup"><span data-stu-id="afa61-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afa61-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="afa61-117">S_OK</span></span>|<span data-ttu-id="afa61-118">`Validate`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="afa61-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="afa61-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="afa61-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="afa61-120">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="afa61-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="afa61-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="afa61-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="afa61-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="afa61-122">The call timed out.</span></span>|  
|<span data-ttu-id="afa61-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="afa61-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="afa61-124">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="afa61-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="afa61-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="afa61-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="afa61-126">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="afa61-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="afa61-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="afa61-127">E_FAIL</span></span>|<span data-ttu-id="afa61-128">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="afa61-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="afa61-129">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="afa61-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="afa61-130">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="afa61-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afa61-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afa61-131">Requirements</span></span>  
 <span data-ttu-id="afa61-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afa61-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa61-133">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="afa61-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="afa61-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afa61-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afa61-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa61-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa61-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="afa61-136">See Also</span></span>  
 [<span data-ttu-id="afa61-137">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afa61-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
