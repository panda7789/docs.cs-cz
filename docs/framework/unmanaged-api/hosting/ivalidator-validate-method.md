---
title: IValidator::Validate – metoda
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765294"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="1232c-102">IValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="1232c-102">IValidator::Validate Method</span></span>
<span data-ttu-id="1232c-103">Ověří zadaný (PE portable executable) nebo soubor Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="1232c-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1232c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1232c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1232c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1232c-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="1232c-106">[in] Ukazatel `IVEHandler` instanci, která zpracovává chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="1232c-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1232c-107">[in] Ukazatel aplikační doménu, ve kterém je soubor načten.</span><span class="sxs-lookup"><span data-stu-id="1232c-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="1232c-108">[in] Bitová kombinace hodnot [validatorflags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty určující, které by se měla provést ověření.</span><span class="sxs-lookup"><span data-stu-id="1232c-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="1232c-109">[in] Maximální počet chyb, aby před ukončením ověření.</span><span class="sxs-lookup"><span data-stu-id="1232c-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="1232c-110">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="1232c-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1232c-111">[in] Řetězec, který určuje název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="1232c-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="1232c-112">[in] Ukazatel do vyrovnávací paměti, ve kterém je soubor uložený.</span><span class="sxs-lookup"><span data-stu-id="1232c-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="1232c-113">[in] Velikost v bajtech, soubor, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="1232c-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1232c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1232c-114">Requirements</span></span>  
 <span data-ttu-id="1232c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1232c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1232c-116">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="1232c-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="1232c-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1232c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1232c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1232c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
