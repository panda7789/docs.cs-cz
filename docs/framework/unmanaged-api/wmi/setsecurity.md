---
title: Funkce SetSecurity (nespravovaný odkaz na rozhraní API)
description: Funkce SetSecurity načte token zosobnění aktuálního vlákna.
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176731"
---
# <a name="setsecurity-function"></a><span data-ttu-id="5ff3f-103">Funkce SetSecurity</span><span class="sxs-lookup"><span data-stu-id="5ff3f-103">SetSecurity function</span></span>

<span data-ttu-id="5ff3f-104">Načte token zosobnění přidružený k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-104">Retrieves the impersonation token associated with the current thread.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5ff3f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ff3f-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a><span data-ttu-id="5ff3f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ff3f-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="5ff3f-107">[out] Když funkce vrátí, obsahuje ukazatel `boolean` na a, který označuje, zda token by měl být resetován voláním [funkce ResetSecurity.](resetsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="5ff3f-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="5ff3f-108">[out] Když funkce vrátí, obsahuje ukazatel na popisovač tokenu zosobnění přidružené ho aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="5ff3f-109">Jeho hodnota `null` může být, pokud neexistuje žádný token přidružený k aktuálnívlákno.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-109">Its value can be `null` if there is no token associated with the current thread.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ff3f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ff3f-110">Return value</span></span>

<span data-ttu-id="5ff3f-111">Pokud je funkce úspěšná, `S_OK` vrácená hodnota je (0).</span><span class="sxs-lookup"><span data-stu-id="5ff3f-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="5ff3f-112">Pokud funkce selže, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5ff3f-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="5ff3f-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="5ff3f-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ff3f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ff3f-114">Requirements</span></span>

 <span data-ttu-id="5ff3f-115">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff3f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="5ff3f-116">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5ff3f-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="5ff3f-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff3f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ff3f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ff3f-118">See also</span></span>

- [<span data-ttu-id="5ff3f-119">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5ff3f-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
