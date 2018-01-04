---
title: "IValidator::FormatEventInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddff0a640f37133bf5a44aea1e371d73d0fd2856
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="78c4f-102">IValidator::FormatEventInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="78c4f-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="78c4f-103">Získá chybovou zprávu odpovídající zadané chybě.</span><span class="sxs-lookup"><span data-stu-id="78c4f-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78c4f-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78c4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78c4f-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="78c4f-106">[v] Hodnota HRESULT, který byl předán na obslužnou rutinu chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="78c4f-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="78c4f-107">[v] A `VEContext` instanci, která obsahuje kontextové informace o chybě ověření.</span><span class="sxs-lookup"><span data-stu-id="78c4f-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="78c4f-108">[ve out] Řetězec, který obsahuje vrácené chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="78c4f-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="78c4f-109">[v] Maximální délka chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="78c4f-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="78c4f-110">[v] Bezpečné pole, které obsahuje další parametry popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="78c4f-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78c4f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78c4f-111">Requirements</span></span>  
 <span data-ttu-id="78c4f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c4f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c4f-113">**Záhlaví:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="78c4f-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="78c4f-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78c4f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78c4f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c4f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c4f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="78c4f-116">See Also</span></span>  
 
