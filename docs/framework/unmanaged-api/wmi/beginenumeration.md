---
title: Funkce BeginEnumeration – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce funkce BeginEnumeration obnoví enumerátor na začátku výčtu
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9699f0cfc4e9fdb989337681b164cc1e703c1e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461257"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="bf9cc-103">Funkce BeginEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="bf9cc-103">BeginEnumeration function</span></span>
<span data-ttu-id="bf9cc-104">Obnoví enumerátor zpět na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bf9cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf9cc-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="bf9cc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf9cc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bf9cc-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="bf9cc-108">`ptr` [v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-108">`ptr` [in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="bf9cc-109">[v] Bitová kombinace příznaků nebo hodnoty, které jsou popsané v [poznámky](#remarks) oddíl, který určuje vlastnosti zahrnuté ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf9cc-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-110">Return value</span></span>

<span data-ttu-id="bf9cc-111">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="bf9cc-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf9cc-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9cc-112">Constant</span></span>  |<span data-ttu-id="bf9cc-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-113">Value</span></span>  |<span data-ttu-id="bf9cc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9cc-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bf9cc-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bf9cc-115">0x80041008</span></span> | <span data-ttu-id="bf9cc-116">Zadaná kombinace příznaků v `lEnumFlags` je neplatný nebo neplatný argument byl zadán.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="bf9cc-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="bf9cc-117">0x8004101d</span></span> | <span data-ttu-id="bf9cc-118">Druhé volání `BeginEnumeration` byl proveden bez použité volání [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bf9cc-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bf9cc-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bf9cc-119">0x80041006</span></span> | <span data-ttu-id="bf9cc-120">Je k dispozici zahájíte nové – výčet není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bf9cc-121">0</span><span class="sxs-lookup"><span data-stu-id="bf9cc-121">0</span></span> | <span data-ttu-id="bf9cc-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bf9cc-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf9cc-123">Remarks</span></span>

<span data-ttu-id="bf9cc-124">Tato funkce zabalí volání [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="bf9cc-125">Příznaky, které lze předat jako `lEnumFlags` argument jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="bf9cc-126">Můžete kombinovat jeden příznak z každé skupiny libovolný příznakem z jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="bf9cc-127">Příznaky ze stejné skupiny jsou však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="bf9cc-128">**Skupina 1**</span><span class="sxs-lookup"><span data-stu-id="bf9cc-128">**Group 1**</span></span>

|<span data-ttu-id="bf9cc-129">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9cc-129">Constant</span></span>  |<span data-ttu-id="bf9cc-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-130">Value</span></span>  |<span data-ttu-id="bf9cc-131">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9cc-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="bf9cc-132">0x4</span><span class="sxs-lookup"><span data-stu-id="bf9cc-132">0x4</span></span> | <span data-ttu-id="bf9cc-133">Obsahovat vlastnosti, které tvoří pouze klíč.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="bf9cc-134">0x8</span><span class="sxs-lookup"><span data-stu-id="bf9cc-134">0x8</span></span> | <span data-ttu-id="bf9cc-135">Obsahovat vlastnosti, které jsou pouze odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="bf9cc-136">**Skupina 2**</span><span class="sxs-lookup"><span data-stu-id="bf9cc-136">**Group 2**</span></span>

<span data-ttu-id="bf9cc-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9cc-137">Constant</span></span>  |<span data-ttu-id="bf9cc-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-138">Value</span></span>  |<span data-ttu-id="bf9cc-139">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9cc-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="bf9cc-140">0x30</span><span class="sxs-lookup"><span data-stu-id="bf9cc-140">0x30</span></span> | <span data-ttu-id="bf9cc-141">Omezte výčtu pouze vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="bf9cc-142">0x40</span><span class="sxs-lookup"><span data-stu-id="bf9cc-142">0x40</span></span> | <span data-ttu-id="bf9cc-143">Obsahovat místní a šířený vlastnosti ale vyloučit vlastnosti systému z výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="bf9cc-144">Pro třídy:</span><span class="sxs-lookup"><span data-stu-id="bf9cc-144">For classes:</span></span>

<span data-ttu-id="bf9cc-145">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9cc-145">Constant</span></span>  |<span data-ttu-id="bf9cc-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-146">Value</span></span>  |<span data-ttu-id="bf9cc-147">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9cc-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="bf9cc-148">0x100</span><span class="sxs-lookup"><span data-stu-id="bf9cc-148">0x100</span></span> | <span data-ttu-id="bf9cc-149">Omezte výčtu vlastnosti přepsání v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="bf9cc-150">0x100</span><span class="sxs-lookup"><span data-stu-id="bf9cc-150">0x100</span></span> | <span data-ttu-id="bf9cc-151">Omezte výčtu vlastnosti přepsání v aktuální definici třídy a vlastnosti nového definovaný ve třídě.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="bf9cc-152">0x300</span><span class="sxs-lookup"><span data-stu-id="bf9cc-152">0x300</span></span> | <span data-ttu-id="bf9cc-153">A maskování (místo příznak) použít proti `lEnumFlags` hodnota ke kontrole, pokud má jedna `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` nastavena.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bf9cc-154">0x10</span><span class="sxs-lookup"><span data-stu-id="bf9cc-154">0x10</span></span> | <span data-ttu-id="bf9cc-155">Omezte výčet vlastností, které jsou definované ani upravit v vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bf9cc-156">0x20</span><span class="sxs-lookup"><span data-stu-id="bf9cc-156">0x20</span></span> | <span data-ttu-id="bf9cc-157">Omezte výčet vlastností, které se dědí z třídy base.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="bf9cc-158">Pro instance:</span><span class="sxs-lookup"><span data-stu-id="bf9cc-158">For instances:</span></span>

<span data-ttu-id="bf9cc-159">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf9cc-159">Constant</span></span>  |<span data-ttu-id="bf9cc-160">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf9cc-160">Value</span></span>  |<span data-ttu-id="bf9cc-161">Popis</span><span class="sxs-lookup"><span data-stu-id="bf9cc-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="bf9cc-162">0x10</span><span class="sxs-lookup"><span data-stu-id="bf9cc-162">0x10</span></span> | <span data-ttu-id="bf9cc-163">Omezte výčet vlastností, které jsou definované ani upravit v vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="bf9cc-164">0x20</span><span class="sxs-lookup"><span data-stu-id="bf9cc-164">0x20</span></span> | <span data-ttu-id="bf9cc-165">Omezte výčet vlastností, které se dědí z třídy base.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="bf9cc-166">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf9cc-166">Requirements</span></span>  
 <span data-ttu-id="bf9cc-167">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9cc-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9cc-168">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf9cc-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bf9cc-169">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9cc-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9cc-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf9cc-170">See also</span></span>  
[<span data-ttu-id="bf9cc-171">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bf9cc-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
