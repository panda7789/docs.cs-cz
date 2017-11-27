---
title: "Funkce CompareTo (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce CompareTo porovná objektu na jiný objekt rozhraní WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CompareTo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CompareTo
helpviewer_keywords: CompareTo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dacb1516bebfc73ae9e16b03f3755ab49382e571
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="compareto-function"></a><span data-ttu-id="f3389-103">CompareTo – funkce</span><span class="sxs-lookup"><span data-stu-id="f3389-103">CompareTo function</span></span>
<span data-ttu-id="f3389-104">Porovná objekt k jinému objektu správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3389-104">Compares an object to another Windows management object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f3389-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3389-105">Syntax</span></span>  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f3389-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3389-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f3389-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f3389-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f3389-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="f3389-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`flags`  
<span data-ttu-id="f3389-109">[v] Bitová kombinace příznaky, které určují vlastnosti objektu vzít v úvahu pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="f3389-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="f3389-110">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="f3389-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`  

<span data-ttu-id="f3389-111">[v] Objekt k porovnání.</span><span class="sxs-lookup"><span data-stu-id="f3389-111">[in] The object for comparison.</span></span> <span data-ttu-id="f3389-112">`pcompareTo`musí být platná [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="f3389-112">`pcompareTo` must be a valid [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f3389-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f3389-113">Return value</span></span>

<span data-ttu-id="f3389-114">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="f3389-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f3389-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f3389-115">Constant</span></span>  |<span data-ttu-id="f3389-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3389-116">Value</span></span>  |<span data-ttu-id="f3389-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f3389-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f3389-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f3389-118">0x80041001</span></span> | <span data-ttu-id="f3389-119">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="f3389-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f3389-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f3389-120">0x80041008</span></span> | <span data-ttu-id="f3389-121">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="f3389-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="f3389-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f3389-122">0x8004101d</span></span> | <span data-ttu-id="f3389-123">Druhé volání `BeginEnumeration` byl proveden bez použité volání [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f3389-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f3389-124">0</span><span class="sxs-lookup"><span data-stu-id="f3389-124">0</span></span> | <span data-ttu-id="f3389-125">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f3389-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="f3389-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="f3389-126">0x40003</span></span> | <span data-ttu-id="f3389-127">Objekty se liší.</span><span class="sxs-lookup"><span data-stu-id="f3389-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="f3389-128">0</span><span class="sxs-lookup"><span data-stu-id="f3389-128">0</span></span> | <span data-ttu-id="f3389-129">Objekty jsou stejné podle příznaky porovnání.</span><span class="sxs-lookup"><span data-stu-id="f3389-129">The objects are the same based on the comparison flags.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f3389-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3389-130">Remarks</span></span>

<span data-ttu-id="f3389-131">Tato funkce zabalí volání [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="f3389-131">This function wraps a call to the [IWbemClassObject::CompareTo](https://msdn.microsoft.com/library/aa391437(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f3389-132">Příznaky, které lze předat jako `lEnumFlags` argument jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="f3389-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="f3389-133">Zadávat lze jednotlivé vlastnosti zahrnutých v porovnání zadáním bitovou kombinaci následující příznaky:</span><span class="sxs-lookup"><span data-stu-id="f3389-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="f3389-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f3389-134">Constant</span></span>  |<span data-ttu-id="f3389-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3389-135">Value</span></span>  |<span data-ttu-id="f3389-136">Popis</span><span class="sxs-lookup"><span data-stu-id="f3389-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="f3389-137">2</span><span class="sxs-lookup"><span data-stu-id="f3389-137">2</span></span> | <span data-ttu-id="f3389-138">Ignorujte zdroje (serveru a oboru názvů, které pocházejí z).</span><span class="sxs-lookup"><span data-stu-id="f3389-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="f3389-139">1</span><span class="sxs-lookup"><span data-stu-id="f3389-139">1</span></span> | <span data-ttu-id="f3389-140">Ignorovat všechny kvalifikátory (včetně **klíč** a **dynamické**)</span><span class="sxs-lookup"><span data-stu-id="f3389-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="f3389-141">4</span><span class="sxs-lookup"><span data-stu-id="f3389-141">4</span></span> | <span data-ttu-id="f3389-142">Ignorujte výchozí hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="f3389-142">Ignore default values of properties.</span></span> <span data-ttu-id="f3389-143">Tento příznak se vztahuje pouze k porovnání tříd.</span><span class="sxs-lookup"><span data-stu-id="f3389-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="f3389-144">0x20</span><span class="sxs-lookup"><span data-stu-id="f3389-144">0x20</span></span> | <span data-ttu-id="f3389-145">Ignorujte kvalifikátor typů.</span><span class="sxs-lookup"><span data-stu-id="f3389-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="f3389-146">Tento příznak stále kvalifikátory bere v úvahu, ale ignoruje příchuť rozdíly, jako například šíření pravidla a přepsání omezení.</span><span class="sxs-lookup"><span data-stu-id="f3389-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="f3389-147">0x10</span><span class="sxs-lookup"><span data-stu-id="f3389-147">0x10</span></span> | <span data-ttu-id="f3389-148">Ignorujte velká písmena v porovnání hodnot řetězců.</span><span class="sxs-lookup"><span data-stu-id="f3389-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="f3389-149">To se vztahuje jak na řetězce a kvalifikátor hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3389-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="f3389-150">Porovnání názvů vlastností a kvalifikátor je vždy bez ohledu na to, jestli je nastavený tento příznak malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f3389-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="f3389-151">0x8</span><span class="sxs-lookup"><span data-stu-id="f3389-151">0x8</span></span> | <span data-ttu-id="f3389-152">Předpokládejme, že porovnávaných objektů jsou instanes stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="f3389-152">Assume that the objects being compared are instanes of the same class.</span></span> <span data-ttu-id="f3389-153">V důsledku toho tento příznak porovná instance informace týkající se jenom.</span><span class="sxs-lookup"><span data-stu-id="f3389-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="f3389-154">Pomocí této příznaků za účelem optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="f3389-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="f3389-155">Pokud objekty nejsou stejné třídy, není definován výsledky.</span><span class="sxs-lookup"><span data-stu-id="f3389-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="f3389-156">Nebo můžete zadat jeden složený příznak následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f3389-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="f3389-157">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f3389-157">Constant</span></span>  |<span data-ttu-id="f3389-158">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3389-158">Value</span></span>  |<span data-ttu-id="f3389-159">Popis</span><span class="sxs-lookup"><span data-stu-id="f3389-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="f3389-160">0</span><span class="sxs-lookup"><span data-stu-id="f3389-160">0</span></span> | <span data-ttu-id="f3389-161">Vezměte v úvahu všechny funkce v porovnání.</span><span class="sxs-lookup"><span data-stu-id="f3389-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="f3389-162">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3389-162">Requirements</span></span>  
 <span data-ttu-id="f3389-163">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3389-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3389-164">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f3389-164">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f3389-165">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f3389-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3389-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3389-166">See also</span></span>  
[<span data-ttu-id="f3389-167">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f3389-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
