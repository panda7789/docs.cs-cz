---
title: IValidator::FormatEventInfo – metoda
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecbecec86d81357000679ab50e12f06d91c9f50d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217078"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="46c6a-102">IValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="46c6a-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="46c6a-103">Získá odpovídající zadaným ověřovéní chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="46c6a-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c6a-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46c6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46c6a-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="46c6a-106">[in] Hodnota HRESULT, který byl předán obslužná rutina chyb ověření.</span><span class="sxs-lookup"><span data-stu-id="46c6a-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="46c6a-107">[in] A `VEContext` instance, která obsahuje kontextové informace o chybě ověření.</span><span class="sxs-lookup"><span data-stu-id="46c6a-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="46c6a-108">[out v] Řetězec, který obsahuje vrácené chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="46c6a-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="46c6a-109">[in] Maximální délka chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="46c6a-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="46c6a-110">[in] Bezpečné pole, která obsahuje další parametry popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="46c6a-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c6a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46c6a-111">Requirements</span></span>  
 <span data-ttu-id="46c6a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c6a-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="46c6a-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="46c6a-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46c6a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46c6a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
