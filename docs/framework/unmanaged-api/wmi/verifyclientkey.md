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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214712"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="f45dd-103">VerifyClientKey – funkce</span><span class="sxs-lookup"><span data-stu-id="f45dd-103">VerifyClientKey function</span></span>
<span data-ttu-id="f45dd-104">Zajistí, že klíč klienta bude mít správné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f45dd-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f45dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f45dd-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="f45dd-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f45dd-106">Return value</span></span>

<span data-ttu-id="f45dd-107">Pokud funkce uspěje, vrácená hodnota je `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="f45dd-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="f45dd-108">Pokud funkce selže, vrácená hodnota je kód chyby definované v *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="f45dd-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="f45dd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f45dd-109">Requirements</span></span>  
 <span data-ttu-id="f45dd-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f45dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f45dd-111">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="f45dd-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="f45dd-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f45dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45dd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f45dd-113">See also</span></span>

- [<span data-ttu-id="f45dd-114">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f45dd-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
