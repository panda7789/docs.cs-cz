---
title: GetErrorInfo – funkce (odkaz na nespravované rozhraní API)
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
ms.openlocfilehash: 062dc62dfe53af3bf5158cb1add0897eccc1df60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102617"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="81470-103">GetErrorInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="81470-103">GetErrorInfo function</span></span>
<span data-ttu-id="81470-104">Načte informace o chybě z předchozího volání funkce.</span><span class="sxs-lookup"><span data-stu-id="81470-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="81470-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81470-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="81470-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="81470-106">Return value</span></span>

<span data-ttu-id="81470-107">Ukazatel na objekt [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) , pokud je volání funkce úspěšné, nebo `null`, pokud selže.</span><span class="sxs-lookup"><span data-stu-id="81470-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="81470-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81470-108">Remarks</span></span>

<span data-ttu-id="81470-109">Tato funkce zalomí volání metody [IComThreadingInfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="81470-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="81470-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81470-110">Requirements</span></span>  
 <span data-ttu-id="81470-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81470-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81470-112">**Hlavička:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="81470-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="81470-113">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81470-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81470-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81470-114">See also</span></span>

- [<span data-ttu-id="81470-115">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="81470-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
