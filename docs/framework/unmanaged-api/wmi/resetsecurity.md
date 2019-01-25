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
ms.openlocfilehash: 2f117b9807d57847d53cf00fbb4983e187798f09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730851"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="9f8a3-103">ResetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="9f8a3-103">ResetSecurity function</span></span>
<span data-ttu-id="9f8a3-104">Přiřadí zadaný zosobnění pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="9f8a3-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9f8a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f8a3-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="9f8a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f8a3-106">Parameters</span></span>

`token`  
<span data-ttu-id="9f8a3-107">[in] Token zosobnění pro přidružení k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="9f8a3-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="9f8a3-108">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="9f8a3-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="9f8a3-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9f8a3-109">Return value</span></span>

<span data-ttu-id="9f8a3-110">Pokud funkce uspěje, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="9f8a3-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="9f8a3-111">Pokud funkce selže, vrácená hodnota je kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9f8a3-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="9f8a3-112">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9f8a3-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9f8a3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f8a3-113">Requirements</span></span>  
 <span data-ttu-id="9f8a3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f8a3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f8a3-115">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9f8a3-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9f8a3-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f8a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f8a3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f8a3-117">See also</span></span>
- [<span data-ttu-id="9f8a3-118">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9f8a3-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
