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
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123273"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="3e07c-102">IValidator::Validate – metoda</span><span class="sxs-lookup"><span data-stu-id="3e07c-102">IValidator::Validate Method</span></span>
<span data-ttu-id="3e07c-103">Ověří zadaný přenos přenositelného spustitelného souboru (PE) nebo jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3e07c-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e07c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e07c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="3e07c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e07c-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="3e07c-106">pro Ukazatel na instanci `IVEHandler`, která zpracovává chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="3e07c-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="3e07c-107">pro Ukazatel na doménu aplikace, ve které je soubor načten.</span><span class="sxs-lookup"><span data-stu-id="3e07c-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="3e07c-108">pro Bitová kombinace hodnot [ValidatorFlags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , která označuje ověření, která by měla být provedena.</span><span class="sxs-lookup"><span data-stu-id="3e07c-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="3e07c-109">pro Maximální počet chyb, které mají být povoleny před ukončením ověřování.</span><span class="sxs-lookup"><span data-stu-id="3e07c-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="3e07c-110">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="3e07c-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="3e07c-111">pro Řetězec, který určuje název souboru, který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="3e07c-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="3e07c-112">pro Ukazatel na vyrovnávací paměť, ve které je soubor uložený.</span><span class="sxs-lookup"><span data-stu-id="3e07c-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="3e07c-113">pro Velikost souboru (v bajtech), který má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="3e07c-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e07c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e07c-114">Requirements</span></span>  
 <span data-ttu-id="3e07c-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e07c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e07c-116">**Hlavička:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="3e07c-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="3e07c-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3e07c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e07c-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e07c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
