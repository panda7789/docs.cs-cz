---
title: "IValidator::Validate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a74249cb806f332b3ae575223f237438da616972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="77d4e-102">IValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="77d4e-102">IValidator::Validate Method</span></span>
<span data-ttu-id="77d4e-103">Ověří zadaný přenosné spustitelný soubor (PE) nebo soubor Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="77d4e-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d4e-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77d4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77d4e-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="77d4e-106">[v] Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="77d4e-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="77d4e-107">[v] Ukazatel na doménu aplikace, ve kterém je načíst soubor.</span><span class="sxs-lookup"><span data-stu-id="77d4e-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="77d4e-108">[v] Bitovou kombinaci [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty, označující objasňuje ověření, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="77d4e-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="77d4e-109">[v] Maximální počet chyb umožňující před ukončením ověření.</span><span class="sxs-lookup"><span data-stu-id="77d4e-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="77d4e-110">[v] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="77d4e-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="77d4e-111">[v] Řetězec, který určuje název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="77d4e-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="77d4e-112">[v] Ukazatel na vyrovnávací paměť, ve kterém je soubor uložený.</span><span class="sxs-lookup"><span data-stu-id="77d4e-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="77d4e-113">[v] Velikost v bajtech, soubor, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="77d4e-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d4e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77d4e-114">Requirements</span></span>  
 <span data-ttu-id="77d4e-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d4e-116">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="77d4e-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="77d4e-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77d4e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77d4e-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d4e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="77d4e-119">See Also</span></span>  
 
