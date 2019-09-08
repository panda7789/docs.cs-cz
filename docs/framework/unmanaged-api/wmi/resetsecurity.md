---
title: ResetSecurity – funkce (Reference nespravovaného rozhraní API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798253"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="5e595-103">ResetSecurity – funkce</span><span class="sxs-lookup"><span data-stu-id="5e595-103">ResetSecurity function</span></span>
<span data-ttu-id="5e595-104">Přiřadí zadaný token zosobnění aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="5e595-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e595-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e595-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="5e595-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e595-106">Parameters</span></span>

`token`  
<span data-ttu-id="5e595-107">pro Token zosobnění, který má být přidružen k aktuálnímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="5e595-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="5e595-108">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="5e595-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="5e595-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5e595-109">Return value</span></span>

<span data-ttu-id="5e595-110">Pokud je funkce úspěšná, vrácená hodnota je `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="5e595-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="5e595-111">Pokud dojde k chybě funkce, vrácená hodnota je nenulový kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5e595-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="5e595-112">Chcete-li získat rozšířené informace o chybě, zavolejte funkci [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="5e595-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="5e595-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e595-113">Requirements</span></span>  
 <span data-ttu-id="5e595-114">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e595-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e595-115">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5e595-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5e595-116">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e595-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e595-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e595-117">See also</span></span>

- [<span data-ttu-id="5e595-118">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5e595-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
