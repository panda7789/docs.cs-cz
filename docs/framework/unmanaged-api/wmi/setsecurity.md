---
title: "Funkce SetSecurity (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce SetSecurity načte token zosobnění aktuální vlákno."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fd7ccb0cfb25773da7e489f9ce4d6332b80a616
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="ce7b5-103">SetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="ce7b5-103">SetSecurity function</span></span>
<span data-ttu-id="ce7b5-104">Načte token zosobnění přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ce7b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce7b5-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="ce7b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce7b5-106">Parameters</span></span>

<span data-ttu-id="ce7b5-107">`pNeedToReset`[out] Když funkce vrátí, obsahuje odkazy `boolean` určující, zda má být token resetovat voláním [ResetSecurity](resetsecurity.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="ce7b5-108">[out] Když funkce vrátí hodnotu, obsahuje ukazatel na popisovač token zosobnění přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="ce7b5-109">Jeho hodnota může být `null` Pokud neexistuje žádné token přidružené k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ce7b5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ce7b5-110">Return value</span></span>

<span data-ttu-id="ce7b5-111">Pokud funkci úspěšné, je vrácenou hodnotu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="ce7b5-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="ce7b5-112">V případě selhání funkce návratovou hodnotu je kód chyby nulová.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="ce7b5-113">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ce7b5-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ce7b5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce7b5-114">Requirements</span></span>  
 <span data-ttu-id="ce7b5-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7b5-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ce7b5-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ce7b5-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ce7b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7b5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce7b5-118">See also</span></span>  
[<span data-ttu-id="ce7b5-119">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ce7b5-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
