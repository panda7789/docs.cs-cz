---
title: Funkce VerifyClientKey (referenční dokumentace nespravovaného rozhraní API)
description: Funkce VerifyClientKey zajistí, že klíč klienta má správné zabezpečení.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47fee26a0c4c25e4bff5bca94e5e26daaf98cccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782483"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="22d1d-103">VerifyClientKey – funkce</span><span class="sxs-lookup"><span data-stu-id="22d1d-103">VerifyClientKey function</span></span>
<span data-ttu-id="22d1d-104">Zajistí, že klíč klienta bude mít správné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="22d1d-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="22d1d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d1d-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="22d1d-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22d1d-106">Return value</span></span>

<span data-ttu-id="22d1d-107">Pokud funkce uspěje, vrácená hodnota je `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="22d1d-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="22d1d-108">Pokud funkce selže, vrácená hodnota je kód chyby definované v *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="22d1d-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="22d1d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d1d-109">Requirements</span></span>  
 <span data-ttu-id="22d1d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d1d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d1d-111">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="22d1d-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="22d1d-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="22d1d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d1d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d1d-113">See also</span></span>

- [<span data-ttu-id="22d1d-114">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="22d1d-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
