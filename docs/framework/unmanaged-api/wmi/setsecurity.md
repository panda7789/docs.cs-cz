---
title: SetSecurity – funkce (Reference nespravovaného rozhraní API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798247"
---
# <a name="setsecurity-function"></a><span data-ttu-id="fdbc8-103">SetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="fdbc8-103">SetSecurity function</span></span>

<span data-ttu-id="fdbc8-104">Načte token zosobnění přidružený k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="fdbc8-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fdbc8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdbc8-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="fdbc8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdbc8-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="fdbc8-107">mimo Když funkce vrátí, obsahuje ukazatel na `boolean` , který označuje, zda má být token resetován voláním funkce [ResetSecurity](resetsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="fdbc8-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="fdbc8-108">mimo Když funkce vrátí, obsahuje ukazatel na popisovač zosobněného tokenu přidruženého k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="fdbc8-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="fdbc8-109">Jeho hodnota může být `null` , pokud k aktuálnímu vláknu není přidružen žádný token.</span><span class="sxs-lookup"><span data-stu-id="fdbc8-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="fdbc8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fdbc8-110">Return value</span></span>

<span data-ttu-id="fdbc8-111">Pokud je funkce úspěšná, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="fdbc8-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="fdbc8-112">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fdbc8-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="fdbc8-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="fdbc8-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="fdbc8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdbc8-114">Requirements</span></span>

 <span data-ttu-id="fdbc8-115">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdbc8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="fdbc8-116">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fdbc8-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="fdbc8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fdbc8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fdbc8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdbc8-118">See also</span></span>

- [<span data-ttu-id="fdbc8-119">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="fdbc8-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
