---
title: VerifyClientKey – funkce (Reference nespravovaného rozhraní API)
description: Funkce VerifyClientKey zajišťuje správné zabezpečení klíče klienta.
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
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798187"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="bd601-103">VerifyClientKey – funkce</span><span class="sxs-lookup"><span data-stu-id="bd601-103">VerifyClientKey function</span></span>
<span data-ttu-id="bd601-104">Zajišťuje, aby měl klíč klienta správné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bd601-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bd601-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd601-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="bd601-106">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd601-106">Return value</span></span>

<span data-ttu-id="bd601-107">Pokud je funkce úspěšná, vrácená hodnota je `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="bd601-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="bd601-108">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód, který je definován v *Winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="bd601-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd601-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd601-109">Requirements</span></span>  
 <span data-ttu-id="bd601-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd601-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd601-111">**Hlaviček** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="bd601-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="bd601-112">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bd601-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd601-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd601-113">See also</span></span>

- [<span data-ttu-id="bd601-114">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bd601-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
