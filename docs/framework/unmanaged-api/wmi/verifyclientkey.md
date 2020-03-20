---
title: Funkce VerifyClientKey (Unmanaged API Reference)
description: Funkce VerifyClientKey zajišťuje, že klientský klíč má správné zabezpečení.
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176705"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="69997-103">Ověřit funkci Klíč klienta</span><span class="sxs-lookup"><span data-stu-id="69997-103">VerifyClientKey function</span></span>
<span data-ttu-id="69997-104">Zajišťuje, že klientský klíč má správné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="69997-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="69997-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69997-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="69997-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="69997-106">Return value</span></span>

<span data-ttu-id="69997-107">Pokud je funkce úspěšná, `ERROR_SUCCESS` vrácená hodnota je (0).</span><span class="sxs-lookup"><span data-stu-id="69997-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="69997-108">Pokud funkce selže, vrácená hodnota je nenulový kód chyby definovaný v *souboru WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="69997-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="69997-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69997-109">Requirements</span></span>  
 <span data-ttu-id="69997-110">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69997-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69997-111">**Záhlaví:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="69997-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="69997-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="69997-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69997-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="69997-113">See also</span></span>

- [<span data-ttu-id="69997-114">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="69997-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
