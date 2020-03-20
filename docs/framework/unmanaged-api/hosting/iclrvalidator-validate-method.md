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
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178065"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="e7a03-102">ICLRValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="e7a03-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="e7a03-103">Ověří přenosný spustitelný soubor (PE) nebo zprostředkující jazyk společnosti Microsoft (MSIL) v zadaném souboru.</span><span class="sxs-lookup"><span data-stu-id="e7a03-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a03-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e7a03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7a03-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="e7a03-106">[v] Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="e7a03-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="e7a03-107">[v] Identifikátor pro aktuální <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e7a03-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="e7a03-108">[v] Kombinace hodnot [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) označující druh ověření, který by měl být proveden.</span><span class="sxs-lookup"><span data-stu-id="e7a03-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="e7a03-109">[v] Maximální počet chyb, které mají být povoleny před ukončením ověření.</span><span class="sxs-lookup"><span data-stu-id="e7a03-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="e7a03-110">[v] Nepoužité.</span><span class="sxs-lookup"><span data-stu-id="e7a03-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e7a03-111">[v] Název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="e7a03-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="e7a03-112">[v] Ukazatel na vyrovnávací paměť souboru.</span><span class="sxs-lookup"><span data-stu-id="e7a03-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="e7a03-113">[v] Velikost souboru, který má být ověřen, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e7a03-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7a03-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e7a03-114">Return Value</span></span>  
  
|<span data-ttu-id="e7a03-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7a03-115">HRESULT</span></span>|<span data-ttu-id="e7a03-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e7a03-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7a03-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7a03-117">S_OK</span></span>|<span data-ttu-id="e7a03-118">`Validate`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e7a03-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="e7a03-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7a03-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7a03-120">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e7a03-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7a03-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7a03-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7a03-122">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="e7a03-122">The call timed out.</span></span>|  
|<span data-ttu-id="e7a03-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7a03-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7a03-124">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e7a03-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7a03-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7a03-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7a03-126">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="e7a03-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7a03-127">E_fail</span><span class="sxs-lookup"><span data-stu-id="e7a03-127">E_FAIL</span></span>|<span data-ttu-id="e7a03-128">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="e7a03-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7a03-129">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e7a03-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7a03-130">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e7a03-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7a03-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7a03-131">Requirements</span></span>  
 <span data-ttu-id="e7a03-132">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a03-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a03-133">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e7a03-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e7a03-134">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7a03-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7a03-135">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a03-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a03-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7a03-136">See also</span></span>

- [<span data-ttu-id="e7a03-137">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7a03-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
