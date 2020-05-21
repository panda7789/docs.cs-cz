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
ms.openlocfilehash: 18492f3e95947a3a11da9d5d303651c04d764a8f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762627"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="0bac8-102">ICLRValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="0bac8-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="0bac8-103">Ověří přenosných spustitelných souborů (PE) nebo jazyka MSIL (Microsoft Intermediate Language) v zadaném souboru.</span><span class="sxs-lookup"><span data-stu-id="0bac8-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bac8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bac8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0bac8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bac8-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="0bac8-106">pro Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="0bac8-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="0bac8-107">pro Identifikátor aktuálního <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="0bac8-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="0bac8-108">pro Kombinace hodnot [ValidatorFlags –](validatorflags-enumeration.md) , které označují druh ověřování, které se má provést.</span><span class="sxs-lookup"><span data-stu-id="0bac8-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="0bac8-109">pro Maximální počet chyb, které mají být povoleny před ukončením ověřování.</span><span class="sxs-lookup"><span data-stu-id="0bac8-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="0bac8-110">pro Nepoužívané.</span><span class="sxs-lookup"><span data-stu-id="0bac8-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="0bac8-111">pro Název souboru, který se má ověřit</span><span class="sxs-lookup"><span data-stu-id="0bac8-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="0bac8-112">pro Ukazatel na vyrovnávací paměť souboru.</span><span class="sxs-lookup"><span data-stu-id="0bac8-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="0bac8-113">pro Velikost souboru (v bajtech), který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="0bac8-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bac8-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bac8-114">Return Value</span></span>  
  
|<span data-ttu-id="0bac8-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bac8-115">HRESULT</span></span>|<span data-ttu-id="0bac8-116">Popis</span><span class="sxs-lookup"><span data-stu-id="0bac8-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bac8-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bac8-117">S_OK</span></span>|<span data-ttu-id="0bac8-118">`Validate`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0bac8-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="0bac8-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0bac8-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0bac8-120">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0bac8-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0bac8-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0bac8-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0bac8-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0bac8-122">The call timed out.</span></span>|  
|<span data-ttu-id="0bac8-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0bac8-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0bac8-124">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0bac8-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0bac8-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0bac8-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0bac8-126">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0bac8-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0bac8-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0bac8-127">E_FAIL</span></span>|<span data-ttu-id="0bac8-128">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0bac8-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0bac8-129">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0bac8-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0bac8-130">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0bac8-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bac8-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bac8-131">Requirements</span></span>  
 <span data-ttu-id="0bac8-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bac8-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bac8-133">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="0bac8-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="0bac8-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0bac8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bac8-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bac8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bac8-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bac8-136">See also</span></span>

- [<span data-ttu-id="0bac8-137">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bac8-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
