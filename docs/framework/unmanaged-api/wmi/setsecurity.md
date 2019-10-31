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
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120215"
---
# <a name="setsecurity-function"></a><span data-ttu-id="614c2-103">SetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="614c2-103">SetSecurity function</span></span>

<span data-ttu-id="614c2-104">Načte token zosobnění přidružený k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="614c2-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="614c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="614c2-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="614c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="614c2-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="614c2-107">mimo Když funkce vrátí, obsahuje ukazatel na `boolean`, který označuje, zda má být token resetován voláním funkce [ResetSecurity](resetsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="614c2-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="614c2-108">mimo Když funkce vrátí, obsahuje ukazatel na popisovač zosobněného tokenu přidruženého k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="614c2-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="614c2-109">Jeho hodnota může být `null`, pokud k aktuálnímu vláknu není přidružen žádný token.</span><span class="sxs-lookup"><span data-stu-id="614c2-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="614c2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="614c2-110">Return value</span></span>

<span data-ttu-id="614c2-111">Pokud je funkce úspěšná, návratová hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="614c2-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="614c2-112">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="614c2-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="614c2-113">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="614c2-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="614c2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="614c2-114">Requirements</span></span>

 <span data-ttu-id="614c2-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="614c2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="614c2-116">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="614c2-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="614c2-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="614c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="614c2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="614c2-118">See also</span></span>

- [<span data-ttu-id="614c2-119">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="614c2-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
