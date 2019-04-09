---
title: Initialize – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Inicializační funkci provádí inicializace rozhraní WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8e87157a7adf45f35608aeba1067f2d66c8972
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081603"
---
# <a name="initialize-function"></a><span data-ttu-id="6d78b-103">Initialize – funkce</span><span class="sxs-lookup"><span data-stu-id="6d78b-103">Initialize function</span></span>
<span data-ttu-id="6d78b-104">Provede inicializaci služby WMI.</span><span class="sxs-lookup"><span data-stu-id="6d78b-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6d78b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d78b-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="6d78b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d78b-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="6d78b-107">[in] `true` k označení, že volání QueryInterface u objektů WMI jsou povoleny. `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="6d78b-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="6d78b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6d78b-108">Return value</span></span>

<span data-ttu-id="6d78b-109">Funkce vždy vrátí `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="6d78b-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="6d78b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d78b-110">Requirements</span></span>  
 <span data-ttu-id="6d78b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d78b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d78b-112">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="6d78b-112">**Header:** WMINet_Utils.def</span></span>  
  
 **<span data-ttu-id="6d78b-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6d78b-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d78b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d78b-114">See also</span></span>

- [<span data-ttu-id="6d78b-115">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6d78b-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
