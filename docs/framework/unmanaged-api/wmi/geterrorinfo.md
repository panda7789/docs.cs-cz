---
title: GetErrorInfo – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetErrorInfo – načte informace o chybě z předchozího volání funkce.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f25777402fa31e72cbbf36f58a6c4cc65542979
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039472"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="f868c-103">GetErrorInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f868c-103">GetErrorInfo function</span></span>
<span data-ttu-id="f868c-104">Načte informace o chybě z předchozího volání funkce.</span><span class="sxs-lookup"><span data-stu-id="f868c-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f868c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f868c-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="f868c-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f868c-106">Return value</span></span>

<span data-ttu-id="f868c-107">Ukazatel na [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) objektu, pokud bude volání funkce úspěšné, nebo `null` Pokud selže.</span><span class="sxs-lookup"><span data-stu-id="f868c-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f868c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f868c-108">Remarks</span></span>

<span data-ttu-id="f868c-109">Tato funkce zalamuje volání na [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.</span><span class="sxs-lookup"><span data-stu-id="f868c-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f868c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f868c-110">Requirements</span></span>  
 <span data-ttu-id="f868c-111">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f868c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f868c-112">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="f868c-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="f868c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f868c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f868c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f868c-114">See also</span></span>  
[<span data-ttu-id="f868c-115">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f868c-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
