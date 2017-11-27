---
title: "Funkce ResetSecurity (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ResetSecurity přiřadí token zosobnění aktuální vlákno."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2790012a429c6a0551d8321a80570f3f8be2142b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="3a699-103">ResetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="3a699-103">ResetSecurity function</span></span>
<span data-ttu-id="3a699-104">Přiřadí token poskytnutý zosobnění aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="3a699-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3a699-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a699-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="3a699-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a699-106">Parameters</span></span>

`token`  
<span data-ttu-id="3a699-107">[v] Token zosobnění pro přidružení aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="3a699-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="3a699-108">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="3a699-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="3a699-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3a699-109">Return value</span></span>

<span data-ttu-id="3a699-110">Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="3a699-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="3a699-111">V případě selhání funkce návratovou hodnotu je kód chyby nulová.</span><span class="sxs-lookup"><span data-stu-id="3a699-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="3a699-112">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="3a699-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="3a699-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a699-113">Requirements</span></span>  
 <span data-ttu-id="3a699-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a699-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a699-115">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3a699-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3a699-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3a699-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a699-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a699-117">See also</span></span>  
[<span data-ttu-id="3a699-118">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="3a699-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
