---
title: Funkce ResetSecurity (nespravovaný odkaz na rozhraní API)
description: Funkce ResetSecurity přiřadí aktuálnímu vláknu token zosobnění.
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174859"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="cefb0-103">Funkce ResetSecurity</span><span class="sxs-lookup"><span data-stu-id="cefb0-103">ResetSecurity function</span></span>
<span data-ttu-id="cefb0-104">Přiřadí zadaný token zosobnění aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="cefb0-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cefb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cefb0-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="cefb0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cefb0-106">Parameters</span></span>

`token`  
<span data-ttu-id="cefb0-107">[v] Token zosobnění přidružit k aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="cefb0-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="cefb0-108">Jeho hodnota `null`může být .</span><span class="sxs-lookup"><span data-stu-id="cefb0-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="cefb0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cefb0-109">Return value</span></span>

<span data-ttu-id="cefb0-110">Pokud je funkce úspěšná, `S_OK` vrácená hodnota je (0).</span><span class="sxs-lookup"><span data-stu-id="cefb0-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="cefb0-111">Pokud funkce selže, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cefb0-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="cefb0-112">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="cefb0-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="cefb0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cefb0-113">Requirements</span></span>  
 <span data-ttu-id="cefb0-114">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cefb0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cefb0-115">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cefb0-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cefb0-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cefb0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefb0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cefb0-117">See also</span></span>

- [<span data-ttu-id="cefb0-118">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="cefb0-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
