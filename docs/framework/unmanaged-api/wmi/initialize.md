---
title: "Initialize – funkce (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce inicializace provádí inicializace rozhraní WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Initialize
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Initialize
helpviewer_keywords: Initialize function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62d959c5dfeac237abb20b86df87ae07a077dbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="initialize-function"></a><span data-ttu-id="38bb0-103">Initialize – funkce</span><span class="sxs-lookup"><span data-stu-id="38bb0-103">Initialize function</span></span>
<span data-ttu-id="38bb0-104">Provede inicializaci rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="38bb0-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="38bb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38bb0-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="38bb0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38bb0-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="38bb0-107">[v] `true` k označení, že jsou povoleny volání QueryInterface na objekty rozhraní WMI; `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="38bb0-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="38bb0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38bb0-108">Return value</span></span>

<span data-ttu-id="38bb0-109">Funkce vždy vrátí hodnotu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="38bb0-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="38bb0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38bb0-110">Requirements</span></span>  
 <span data-ttu-id="38bb0-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38bb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38bb0-112">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="38bb0-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="38bb0-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38bb0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bb0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="38bb0-114">See also</span></span>  
[<span data-ttu-id="38bb0-115">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="38bb0-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
