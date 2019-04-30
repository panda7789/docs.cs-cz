---
title: Funkce SetSecurity (referenční dokumentace nespravovaného rozhraní API)
description: Funkce SetSecurity získá token zosobnění aktuální vlákno.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7200e3a19fcadabb5e149c38b620b3f60907c392
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948535"
---
# <a name="setsecurity-function"></a><span data-ttu-id="51479-103">SetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="51479-103">SetSecurity function</span></span>

<span data-ttu-id="51479-104">Získá token zosobnění spojený s aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="51479-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="51479-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51479-105">Syntax</span></span>

```
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="51479-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="51479-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="51479-107">[out] Když funkce vrátí, obsahuje ukazatel na `boolean` , která označuje, zda tento token by se měla obnovit voláním [ResetSecurity](resetsecurity.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="51479-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="51479-108">[out] Když funkce vrátí, obsahuje ukazatel na popisovač token zosobnění spojený s aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="51479-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="51479-109">Jeho hodnota může být `null` Pokud neexistuje žádný token spojené s aktuálním vláknem.</span><span class="sxs-lookup"><span data-stu-id="51479-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="51479-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51479-110">Return value</span></span>

<span data-ttu-id="51479-111">Pokud funkce uspěje, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="51479-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="51479-112">Pokud funkce selže, vrácená hodnota je kód chyby.</span><span class="sxs-lookup"><span data-stu-id="51479-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="51479-113">Chcete-li získat rozšířené informace o chybě, zavolejte [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="51479-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="51479-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51479-114">Requirements</span></span>

 <span data-ttu-id="51479-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51479-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="51479-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51479-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="51479-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="51479-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="51479-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51479-118">See also</span></span>

- [<span data-ttu-id="51479-119">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="51479-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)