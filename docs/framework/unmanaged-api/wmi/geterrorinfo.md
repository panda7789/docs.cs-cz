---
title: "GetErrorInfo – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "GetErrorInfo – funkce načte informace o chybě z předchozího volání funkce."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4b4acde080c61fbfd5cec319c1986b8c86352c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="27fbb-103">GetErrorInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="27fbb-103">GetErrorInfo function</span></span>
<span data-ttu-id="27fbb-104">Načte informace o chybě z předchozího volání funkce.</span><span class="sxs-lookup"><span data-stu-id="27fbb-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="27fbb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27fbb-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="27fbb-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27fbb-106">Return value</span></span>

<span data-ttu-id="27fbb-107">Ukazatel na [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) objektu, pokud je úspěšné volání funkce, nebo `null` Pokud selže.</span><span class="sxs-lookup"><span data-stu-id="27fbb-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="27fbb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27fbb-108">Remarks</span></span>

<span data-ttu-id="27fbb-109">Tato funkce zabalí volání [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="27fbb-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="27fbb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27fbb-110">Requirements</span></span>  
 <span data-ttu-id="27fbb-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27fbb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27fbb-112">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="27fbb-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="27fbb-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27fbb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fbb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="27fbb-114">See also</span></span>  
[<span data-ttu-id="27fbb-115">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="27fbb-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
