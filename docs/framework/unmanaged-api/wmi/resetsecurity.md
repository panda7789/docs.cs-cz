---
title: Funkce ResetSecurity (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ResetSecurity přiřadí token zosobnění pro aktuální vlákno.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e937690c184d810549e8ab11ef1fc2273a45c5f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115125"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="32882-103">ResetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="32882-103">ResetSecurity function</span></span>
<span data-ttu-id="32882-104">Přiřadí zadaný zosobnění pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="32882-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="32882-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32882-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="32882-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="32882-106">Parameters</span></span>

`token`  
<span data-ttu-id="32882-107">[in] Token zosobnění pro přidružení k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="32882-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="32882-108">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="32882-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="32882-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32882-109">Return value</span></span>

<span data-ttu-id="32882-110">Pokud funkce uspěje, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="32882-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="32882-111">Pokud funkce selže, vrácená hodnota je kód chyby.</span><span class="sxs-lookup"><span data-stu-id="32882-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="32882-112">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="32882-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="32882-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32882-113">Requirements</span></span>  
 <span data-ttu-id="32882-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32882-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32882-115">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="32882-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="32882-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32882-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32882-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32882-117">See also</span></span>

- [<span data-ttu-id="32882-118">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="32882-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
