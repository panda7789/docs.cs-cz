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
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459561"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="9e006-103">VerifyClientKey – funkce</span><span class="sxs-lookup"><span data-stu-id="9e006-103">VerifyClientKey function</span></span>
<span data-ttu-id="9e006-104">Zajišťuje, že klíč klienta má správné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9e006-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9e006-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e006-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="9e006-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e006-106">Return value</span></span>

<span data-ttu-id="9e006-107">Pokud funkci úspěšné, je vrácenou hodnotu `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="9e006-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="9e006-108">V případě selhání funkce návratová hodnota je kód chyby nenulové definované v *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="9e006-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e006-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e006-109">Requirements</span></span>  
 <span data-ttu-id="9e006-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e006-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e006-111">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="9e006-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="9e006-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9e006-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e006-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e006-113">See also</span></span>  
[<span data-ttu-id="9e006-114">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9e006-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
