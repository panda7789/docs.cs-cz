---
title: GetErrorInfo (Nespravovaný odkaz na rozhraní API)
description: Funkce GetErrorInfo načte informace o chybě z předchozího volání funkce.
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
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176809"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="099a5-103">GetErrorInfo</span><span class="sxs-lookup"><span data-stu-id="099a5-103">GetErrorInfo function</span></span>
<span data-ttu-id="099a5-104">Načte informace o chybě z předchozího volání funkce.</span><span class="sxs-lookup"><span data-stu-id="099a5-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="099a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="099a5-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="099a5-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="099a5-106">Return value</span></span>

<span data-ttu-id="099a5-107">Ukazatel na objekt [IErrorInfo,](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) pokud je volání `null` funkce úspěšné nebo pokud se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="099a5-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="099a5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="099a5-108">Remarks</span></span>

<span data-ttu-id="099a5-109">Tato funkce zabalí volání metody [IComThreadingInfo::GetErrorInfo.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="099a5-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="099a5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="099a5-110">Requirements</span></span>  
 <span data-ttu-id="099a5-111">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="099a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099a5-112">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="099a5-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="099a5-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="099a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099a5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="099a5-114">See also</span></span>

- [<span data-ttu-id="099a5-115">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="099a5-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
