---
title: Funkce BeginEnumeration (Unmanaged API Reference)
description: Funkce BeginEnumeration resetuje čítač výčtu na začátek výčtu.
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176874"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="3c6db-103">Funkce BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="3c6db-103">BeginEnumeration function</span></span>
<span data-ttu-id="3c6db-104">Obnoví čítač výčtu zpět na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="3c6db-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3c6db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c6db-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="3c6db-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c6db-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3c6db-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="3c6db-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3c6db-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="3c6db-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="3c6db-109">[v] Bitová kombinace příznaků nebo hodnot popsaných v části [Poznámky,](#remarks) která řídí vlastnosti zahrnuté ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="3c6db-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3c6db-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-110">Return value</span></span>

<span data-ttu-id="3c6db-111">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="3c6db-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3c6db-112">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3c6db-112">Constant</span></span>  |<span data-ttu-id="3c6db-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-113">Value</span></span>  |<span data-ttu-id="3c6db-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3c6db-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3c6db-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3c6db-115">0x80041008</span></span> | <span data-ttu-id="3c6db-116">Kombinace příznaků v `lEnumFlags` aplikaci je neplatná nebo byl zadán neplatný argument.</span><span class="sxs-lookup"><span data-stu-id="3c6db-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="3c6db-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="3c6db-117">0x8004101d</span></span> | <span data-ttu-id="3c6db-118">Druhé volání `BeginEnumeration` bylo provedeno bez zasahování volání [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3c6db-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3c6db-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3c6db-119">0x80041006</span></span> | <span data-ttu-id="3c6db-120">Není k dispozici dostatek paměti pro zahájení nového výčtu.</span><span class="sxs-lookup"><span data-stu-id="3c6db-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3c6db-121">0</span><span class="sxs-lookup"><span data-stu-id="3c6db-121">0</span></span> | <span data-ttu-id="3c6db-122">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="3c6db-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3c6db-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c6db-123">Remarks</span></span>

<span data-ttu-id="3c6db-124">Tato funkce zabalí volání [metody IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="3c6db-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="3c6db-125">Příznaky, které mohou být `lEnumFlags` předány jako argument jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="3c6db-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="3c6db-126">Můžete kombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="3c6db-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="3c6db-127">Příznaky ze stejné skupiny se však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="3c6db-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="3c6db-128">**Skupina 1**</span><span class="sxs-lookup"><span data-stu-id="3c6db-128">**Group 1**</span></span>

|<span data-ttu-id="3c6db-129">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3c6db-129">Constant</span></span>  |<span data-ttu-id="3c6db-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-130">Value</span></span>  |<span data-ttu-id="3c6db-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3c6db-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="3c6db-132">0x4</span><span class="sxs-lookup"><span data-stu-id="3c6db-132">0x4</span></span> | <span data-ttu-id="3c6db-133">Zahrnout vlastnosti, které tvoří pouze klíč.</span><span class="sxs-lookup"><span data-stu-id="3c6db-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="3c6db-134">0x8</span><span class="sxs-lookup"><span data-stu-id="3c6db-134">0x8</span></span> | <span data-ttu-id="3c6db-135">Zahrnout vlastnosti, které jsou pouze odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="3c6db-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="3c6db-136">**Skupina 2**</span><span class="sxs-lookup"><span data-stu-id="3c6db-136">**Group 2**</span></span>

<span data-ttu-id="3c6db-137">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3c6db-137">Constant</span></span>  |<span data-ttu-id="3c6db-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-138">Value</span></span>  |<span data-ttu-id="3c6db-139">Popis</span><span class="sxs-lookup"><span data-stu-id="3c6db-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="3c6db-140">0x30</span><span class="sxs-lookup"><span data-stu-id="3c6db-140">0x30</span></span> | <span data-ttu-id="3c6db-141">Omezte výčet pouze na systémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3c6db-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="3c6db-142">0x40</span><span class="sxs-lookup"><span data-stu-id="3c6db-142">0x40</span></span> | <span data-ttu-id="3c6db-143">Zahrnout místní a rozšířené vlastnosti, ale vyloučit vlastnosti systému z výčtu.</span><span class="sxs-lookup"><span data-stu-id="3c6db-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="3c6db-144">Pro třídy:</span><span class="sxs-lookup"><span data-stu-id="3c6db-144">For classes:</span></span>

<span data-ttu-id="3c6db-145">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3c6db-145">Constant</span></span>  |<span data-ttu-id="3c6db-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-146">Value</span></span>  |<span data-ttu-id="3c6db-147">Popis</span><span class="sxs-lookup"><span data-stu-id="3c6db-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="3c6db-148">0x100</span><span class="sxs-lookup"><span data-stu-id="3c6db-148">0x100</span></span> | <span data-ttu-id="3c6db-149">Omezte výčet na vlastnosti přepsané v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="3c6db-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="3c6db-150">0x100</span><span class="sxs-lookup"><span data-stu-id="3c6db-150">0x100</span></span> | <span data-ttu-id="3c6db-151">Omezte výčet na vlastnosti přepsané v aktuální definici třídy a na nové vlastnosti definované ve třídě.</span><span class="sxs-lookup"><span data-stu-id="3c6db-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="3c6db-152">0x300</span><span class="sxs-lookup"><span data-stu-id="3c6db-152">0x300</span></span> | <span data-ttu-id="3c6db-153">Maska (spíše než příznak) použít `lEnumFlags` proti hodnotu `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` zkontrolovat, zda buď nebo je nastavena.</span><span class="sxs-lookup"><span data-stu-id="3c6db-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3c6db-154">0x10</span><span class="sxs-lookup"><span data-stu-id="3c6db-154">0x10</span></span> | <span data-ttu-id="3c6db-155">Omezte výčet na vlastnosti, které jsou definovány nebo změněny v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="3c6db-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="3c6db-156">0x20</span><span class="sxs-lookup"><span data-stu-id="3c6db-156">0x20</span></span> | <span data-ttu-id="3c6db-157">Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="3c6db-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="3c6db-158">Například:</span><span class="sxs-lookup"><span data-stu-id="3c6db-158">For instances:</span></span>

<span data-ttu-id="3c6db-159">Trvalé</span><span class="sxs-lookup"><span data-stu-id="3c6db-159">Constant</span></span>  |<span data-ttu-id="3c6db-160">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c6db-160">Value</span></span>  |<span data-ttu-id="3c6db-161">Popis</span><span class="sxs-lookup"><span data-stu-id="3c6db-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3c6db-162">0x10</span><span class="sxs-lookup"><span data-stu-id="3c6db-162">0x10</span></span> | <span data-ttu-id="3c6db-163">Omezte výčet na vlastnosti, které jsou definovány nebo změněny v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="3c6db-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="3c6db-164">0x20</span><span class="sxs-lookup"><span data-stu-id="3c6db-164">0x20</span></span> | <span data-ttu-id="3c6db-165">Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="3c6db-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3c6db-166">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c6db-166">Requirements</span></span>  
 <span data-ttu-id="3c6db-167">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c6db-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c6db-168">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3c6db-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3c6db-169">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3c6db-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6db-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c6db-170">See also</span></span>

- [<span data-ttu-id="3c6db-171">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="3c6db-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
