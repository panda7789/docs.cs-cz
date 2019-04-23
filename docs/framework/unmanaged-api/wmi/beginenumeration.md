---
title: Funkce BeginEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce BeginEnumeration návrat na začátek výčtu enumerátor
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
ms.openlocfilehash: 4221dbea2b5ad98f889e04eb8a9b6d992b59066e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212294"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="35517-103">Funkce BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="35517-103">BeginEnumeration function</span></span>
<span data-ttu-id="35517-104">Obnoví enumerátor zpět na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="35517-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="35517-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35517-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="35517-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="35517-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="35517-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="35517-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="35517-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="35517-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="35517-109">[in] Bitová kombinace příznaků nebo podle hodnoty [poznámky](#remarks) oddíl, který řídí vlastností obsažených ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="35517-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="35517-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="35517-110">Return value</span></span>

<span data-ttu-id="35517-111">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="35517-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="35517-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="35517-112">Constant</span></span>  |<span data-ttu-id="35517-113">Value</span><span class="sxs-lookup"><span data-stu-id="35517-113">Value</span></span>  |<span data-ttu-id="35517-114">Popis</span><span class="sxs-lookup"><span data-stu-id="35517-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="35517-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="35517-115">0x80041008</span></span> | <span data-ttu-id="35517-116">Kombinace příznaků v `lEnumFlags` není platný nebo neplatný argument byl zadán.</span><span class="sxs-lookup"><span data-stu-id="35517-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="35517-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="35517-117">0x8004101d</span></span> | <span data-ttu-id="35517-118">Druhé volání `BeginEnumeration` proběhla bez opětovné volání [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="35517-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="35517-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="35517-119">0x80041006</span></span> | <span data-ttu-id="35517-120">Nedostatek paměti je k dispozici zahájíte nový výčet.</span><span class="sxs-lookup"><span data-stu-id="35517-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="35517-121">0</span><span class="sxs-lookup"><span data-stu-id="35517-121">0</span></span> | <span data-ttu-id="35517-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="35517-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="35517-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35517-123">Remarks</span></span>

<span data-ttu-id="35517-124">Tato funkce zalamuje volání na [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.</span><span class="sxs-lookup"><span data-stu-id="35517-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="35517-125">Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="35517-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="35517-126">Můžete kombinovat jeden příznak z každé skupiny s všechny příznaky z jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="35517-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="35517-127">Ale příznaky ze stejné skupiny se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="35517-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="35517-128">**Skupina 1**</span><span class="sxs-lookup"><span data-stu-id="35517-128">**Group 1**</span></span>

|<span data-ttu-id="35517-129">Konstanta</span><span class="sxs-lookup"><span data-stu-id="35517-129">Constant</span></span>  |<span data-ttu-id="35517-130">Value</span><span class="sxs-lookup"><span data-stu-id="35517-130">Value</span></span>  |<span data-ttu-id="35517-131">Popis</span><span class="sxs-lookup"><span data-stu-id="35517-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="35517-132">0x4</span><span class="sxs-lookup"><span data-stu-id="35517-132">0x4</span></span> | <span data-ttu-id="35517-133">Obsahovat vlastnosti, které tvoří pouze klíč.</span><span class="sxs-lookup"><span data-stu-id="35517-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="35517-134">0x8</span><span class="sxs-lookup"><span data-stu-id="35517-134">0x8</span></span> | <span data-ttu-id="35517-135">Zahrnují vlastnosti, které jsou pouze odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="35517-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="35517-136">**Skupina 2**</span><span class="sxs-lookup"><span data-stu-id="35517-136">**Group 2**</span></span>

<span data-ttu-id="35517-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="35517-137">Constant</span></span>  |<span data-ttu-id="35517-138">Value</span><span class="sxs-lookup"><span data-stu-id="35517-138">Value</span></span>  |<span data-ttu-id="35517-139">Popis</span><span class="sxs-lookup"><span data-stu-id="35517-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="35517-140">0x30</span><span class="sxs-lookup"><span data-stu-id="35517-140">0x30</span></span> | <span data-ttu-id="35517-141">Omezte výčet pouze vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="35517-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="35517-142">0x40</span><span class="sxs-lookup"><span data-stu-id="35517-142">0x40</span></span> | <span data-ttu-id="35517-143">Zahrnují vlastnosti místní a rozšíří ale vyloučit vlastnosti systému z výčtu.</span><span class="sxs-lookup"><span data-stu-id="35517-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="35517-144">Pro třídy:</span><span class="sxs-lookup"><span data-stu-id="35517-144">For classes:</span></span>

<span data-ttu-id="35517-145">Konstanta</span><span class="sxs-lookup"><span data-stu-id="35517-145">Constant</span></span>  |<span data-ttu-id="35517-146">Value</span><span class="sxs-lookup"><span data-stu-id="35517-146">Value</span></span>  |<span data-ttu-id="35517-147">Popis</span><span class="sxs-lookup"><span data-stu-id="35517-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="35517-148">0x100</span><span class="sxs-lookup"><span data-stu-id="35517-148">0x100</span></span> | <span data-ttu-id="35517-149">Omezte výčet vlastností přepsat v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="35517-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="35517-150">0x100</span><span class="sxs-lookup"><span data-stu-id="35517-150">0x100</span></span> | <span data-ttu-id="35517-151">Omezte výčet vlastností přepsat v aktuální definici třídy a nové vlastnosti definované ve třídě.</span><span class="sxs-lookup"><span data-stu-id="35517-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="35517-152">0x300</span><span class="sxs-lookup"><span data-stu-id="35517-152">0x300</span></span> | <span data-ttu-id="35517-153">A maskování (místo příznak) Chcete-li použít proti `lEnumFlags` hodnotu a zkontrolujte, zda buď `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` nastavena.</span><span class="sxs-lookup"><span data-stu-id="35517-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="35517-154">0x10</span><span class="sxs-lookup"><span data-stu-id="35517-154">0x10</span></span> | <span data-ttu-id="35517-155">Omezte výčet vlastností, které jsou definovány nebo upraveny v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="35517-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="35517-156">0x20</span><span class="sxs-lookup"><span data-stu-id="35517-156">0x20</span></span> | <span data-ttu-id="35517-157">Omezte výčet vlastností, které se dědí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="35517-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="35517-158">Pro instance:</span><span class="sxs-lookup"><span data-stu-id="35517-158">For instances:</span></span>

<span data-ttu-id="35517-159">Konstanta</span><span class="sxs-lookup"><span data-stu-id="35517-159">Constant</span></span>  |<span data-ttu-id="35517-160">Hodnota</span><span class="sxs-lookup"><span data-stu-id="35517-160">Value</span></span>  |<span data-ttu-id="35517-161">Popis</span><span class="sxs-lookup"><span data-stu-id="35517-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="35517-162">0x10</span><span class="sxs-lookup"><span data-stu-id="35517-162">0x10</span></span> | <span data-ttu-id="35517-163">Omezte výčet vlastností, které jsou definovány nebo upraveny v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="35517-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="35517-164">0x20</span><span class="sxs-lookup"><span data-stu-id="35517-164">0x20</span></span> | <span data-ttu-id="35517-165">Omezte výčet vlastností, které se dědí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="35517-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="35517-166">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35517-166">Requirements</span></span>  
 <span data-ttu-id="35517-167">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35517-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35517-168">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="35517-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="35517-169">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="35517-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35517-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35517-170">See also</span></span>

- [<span data-ttu-id="35517-171">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="35517-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)