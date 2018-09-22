---
title: Funkce CompareTo (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CompareTo porovná objekt na jiný objekt rozhraní WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580275"
---
# <a name="compareto-function"></a><span data-ttu-id="98333-103">Funkce CompareTo</span><span class="sxs-lookup"><span data-stu-id="98333-103">CompareTo function</span></span>
<span data-ttu-id="98333-104">Porovná objekt na jiný objekt správy Windows.</span><span class="sxs-lookup"><span data-stu-id="98333-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="98333-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98333-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="98333-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98333-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98333-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="98333-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98333-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="98333-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`  
<span data-ttu-id="98333-109">[in] Bitová kombinace příznaků, které určují vlastnosti objektu vzít v úvahu pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="98333-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="98333-110">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="98333-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="98333-111">[in] Objekt k porovnání.</span><span class="sxs-lookup"><span data-stu-id="98333-111">[in] The object for comparison.</span></span> <span data-ttu-id="98333-112">`pcompareTo` musí být platný [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="98333-112">`pcompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="98333-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98333-113">Return value</span></span>

<span data-ttu-id="98333-114">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="98333-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="98333-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="98333-115">Constant</span></span>  |<span data-ttu-id="98333-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="98333-116">Value</span></span>  |<span data-ttu-id="98333-117">Popis</span><span class="sxs-lookup"><span data-stu-id="98333-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="98333-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="98333-118">0x80041001</span></span> | <span data-ttu-id="98333-119">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="98333-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="98333-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="98333-120">0x80041008</span></span> | <span data-ttu-id="98333-121">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="98333-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="98333-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="98333-122">0x8004101d</span></span> | <span data-ttu-id="98333-123">Druhé volání `BeginEnumeration` proběhla bez opětovné volání [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="98333-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="98333-124">0</span><span class="sxs-lookup"><span data-stu-id="98333-124">0</span></span> | <span data-ttu-id="98333-125">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="98333-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="98333-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="98333-126">0x40003</span></span> | <span data-ttu-id="98333-127">Objekty jsou odlišné.</span><span class="sxs-lookup"><span data-stu-id="98333-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="98333-128">0</span><span class="sxs-lookup"><span data-stu-id="98333-128">0</span></span> | <span data-ttu-id="98333-129">Objekty jsou stejné založené na porovnání příznaky.</span><span class="sxs-lookup"><span data-stu-id="98333-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="98333-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98333-130">Remarks</span></span>

<span data-ttu-id="98333-131">Tato funkce zalamuje volání na [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) metody.</span><span class="sxs-lookup"><span data-stu-id="98333-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="98333-132">Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="98333-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="98333-133">Vlastnosti jednotlivých součástí porovnání můžete zadat tak, že zadáte bitová kombinace hodnot následující příznaky:</span><span class="sxs-lookup"><span data-stu-id="98333-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="98333-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="98333-134">Constant</span></span>  |<span data-ttu-id="98333-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="98333-135">Value</span></span>  |<span data-ttu-id="98333-136">Popis</span><span class="sxs-lookup"><span data-stu-id="98333-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="98333-137">2</span><span class="sxs-lookup"><span data-stu-id="98333-137">2</span></span> | <span data-ttu-id="98333-138">Ignorujte zdroje (serveru a oboru názvů, které pocházejí z).</span><span class="sxs-lookup"><span data-stu-id="98333-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="98333-139">1</span><span class="sxs-lookup"><span data-stu-id="98333-139">1</span></span> | <span data-ttu-id="98333-140">Ignorovat všechny kvalifikátory (včetně **klíč** a **dynamické**)</span><span class="sxs-lookup"><span data-stu-id="98333-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="98333-141">4</span><span class="sxs-lookup"><span data-stu-id="98333-141">4</span></span> | <span data-ttu-id="98333-142">Ignorujte výchozí hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98333-142">Ignore default values of properties.</span></span> <span data-ttu-id="98333-143">Tento příznak platí jenom pro porovnání třídy.</span><span class="sxs-lookup"><span data-stu-id="98333-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="98333-144">0x20</span><span class="sxs-lookup"><span data-stu-id="98333-144">0x20</span></span> | <span data-ttu-id="98333-145">Ignorujte flavor.</span><span class="sxs-lookup"><span data-stu-id="98333-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="98333-146">Tento příznak stále kvalifikátory bere v úvahu, ale bude ignorovat rozdíly charakter, jako jsou pravidla pro šíření a přepsat omezení.</span><span class="sxs-lookup"><span data-stu-id="98333-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="98333-147">0x10</span><span class="sxs-lookup"><span data-stu-id="98333-147">0x10</span></span> | <span data-ttu-id="98333-148">Ignorujte velikost písmen v porovnání hodnot řetězců.</span><span class="sxs-lookup"><span data-stu-id="98333-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="98333-149">Platí to i na řetězce a jednu hodnotu kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="98333-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="98333-150">Porovnání názvy vlastností a kvalifikátor je vždy bez ohledu na to, zda je tento příznak nastaven malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="98333-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="98333-151">0x8</span><span class="sxs-lookup"><span data-stu-id="98333-151">0x8</span></span> | <span data-ttu-id="98333-152">Předpokládají, že jsou objekty, který se porovnává instanes stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="98333-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="98333-153">V důsledku toho tento příznak porovnává instance informace týkající se pouze.</span><span class="sxs-lookup"><span data-stu-id="98333-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="98333-154">Pomocí tohoto příznaku za účelem optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="98333-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="98333-155">Pokud objekty nejsou stejné třídy, nejsou výsledky definovány.</span><span class="sxs-lookup"><span data-stu-id="98333-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="98333-156">Nebo můžete zadat jeden složený příznak následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="98333-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="98333-157">Konstanta</span><span class="sxs-lookup"><span data-stu-id="98333-157">Constant</span></span>  |<span data-ttu-id="98333-158">Hodnota</span><span class="sxs-lookup"><span data-stu-id="98333-158">Value</span></span>  |<span data-ttu-id="98333-159">Popis</span><span class="sxs-lookup"><span data-stu-id="98333-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="98333-160">0</span><span class="sxs-lookup"><span data-stu-id="98333-160">0</span></span> | <span data-ttu-id="98333-161">Vezměte v úvahu všechny funkce v porovnání.</span><span class="sxs-lookup"><span data-stu-id="98333-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="98333-162">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98333-162">Requirements</span></span>  
 <span data-ttu-id="98333-163">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98333-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98333-164">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="98333-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98333-165">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98333-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98333-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98333-166">See also</span></span>  
[<span data-ttu-id="98333-167">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="98333-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
