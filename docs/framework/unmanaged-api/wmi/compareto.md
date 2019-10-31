---
title: CompareTo – funkce (Reference nespravovaného rozhraní API)
description: Funkce CompareTo porovná objekt s jiným objektem WMI.
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
ms.openlocfilehash: 0d210795016cd2e0179b902a224ca0c62f4ac01f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128697"
---
# <a name="compareto-function"></a><span data-ttu-id="67f85-103">Funkce CompareTo</span><span class="sxs-lookup"><span data-stu-id="67f85-103">CompareTo function</span></span>

<span data-ttu-id="67f85-104">Porovná objekt s jiným objektem správy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="67f85-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="67f85-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67f85-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="67f85-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="67f85-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="67f85-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="67f85-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="67f85-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="67f85-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="67f85-109">pro Bitová kombinace příznaků, které určují vlastnosti objektu, které je třeba vzít v úvahu pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="67f85-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="67f85-110">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="67f85-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="67f85-111">pro Objekt pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="67f85-111">[in] The object for comparison.</span></span> <span data-ttu-id="67f85-112">`pCompareTo` musí být platná instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ; nedá se `null`.</span><span class="sxs-lookup"><span data-stu-id="67f85-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="67f85-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="67f85-113">Return value</span></span>

<span data-ttu-id="67f85-114">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="67f85-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="67f85-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="67f85-115">Constant</span></span>  |<span data-ttu-id="67f85-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67f85-116">Value</span></span>  |<span data-ttu-id="67f85-117">Popis</span><span class="sxs-lookup"><span data-stu-id="67f85-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="67f85-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="67f85-118">0x80041001</span></span> | <span data-ttu-id="67f85-119">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="67f85-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="67f85-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="67f85-120">0x80041008</span></span> | <span data-ttu-id="67f85-121">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="67f85-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="67f85-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="67f85-122">0x8004101d</span></span> | <span data-ttu-id="67f85-123">Druhé volání `BeginEnumeration` bylo provedeno bez navýšení volání [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="67f85-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="67f85-124">0,8</span><span class="sxs-lookup"><span data-stu-id="67f85-124">0</span></span> | <span data-ttu-id="67f85-125">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="67f85-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="67f85-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="67f85-126">0x40003</span></span> | <span data-ttu-id="67f85-127">Objekty jsou odlišné.</span><span class="sxs-lookup"><span data-stu-id="67f85-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="67f85-128">0,8</span><span class="sxs-lookup"><span data-stu-id="67f85-128">0</span></span> | <span data-ttu-id="67f85-129">Objekty jsou stejné na základě příznaků porovnávání.</span><span class="sxs-lookup"><span data-stu-id="67f85-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="67f85-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67f85-130">Remarks</span></span>

<span data-ttu-id="67f85-131">Tato funkce zalomí volání metody [IWbemclassObject:: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .</span><span class="sxs-lookup"><span data-stu-id="67f85-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="67f85-132">Příznaky, které mohou být předány jako argument `lEnumFlags`, jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="67f85-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="67f85-133">Můžete určit jednotlivé charakteristiky, které se týkají porovnání, zadáním bitové kombinace následujících příznaků:</span><span class="sxs-lookup"><span data-stu-id="67f85-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="67f85-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="67f85-134">Constant</span></span>  |<span data-ttu-id="67f85-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67f85-135">Value</span></span>  |<span data-ttu-id="67f85-136">Popis</span><span class="sxs-lookup"><span data-stu-id="67f85-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="67f85-137">odst</span><span class="sxs-lookup"><span data-stu-id="67f85-137">2</span></span> | <span data-ttu-id="67f85-138">Ignorujte zdroj (Server a obor názvů, ze kterého pochází).</span><span class="sxs-lookup"><span data-stu-id="67f85-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="67f85-139">první</span><span class="sxs-lookup"><span data-stu-id="67f85-139">1</span></span> | <span data-ttu-id="67f85-140">Ignorovat všechny kvalifikátory (včetně **klíčového** a **dynamického**)</span><span class="sxs-lookup"><span data-stu-id="67f85-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="67f85-141">4</span><span class="sxs-lookup"><span data-stu-id="67f85-141">4</span></span> | <span data-ttu-id="67f85-142">Ignoruje výchozí hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="67f85-142">Ignore default values of properties.</span></span> <span data-ttu-id="67f85-143">Tento příznak se vztahuje pouze na porovnání tříd.</span><span class="sxs-lookup"><span data-stu-id="67f85-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="67f85-144">0x20</span><span class="sxs-lookup"><span data-stu-id="67f85-144">0x20</span></span> | <span data-ttu-id="67f85-145">Ignorovat charakter kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="67f85-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="67f85-146">Tento příznak stále používá kvalifikátory, ale ignoruje rozdíly v charakteru, jako jsou pravidla šíření a omezení přepisování.</span><span class="sxs-lookup"><span data-stu-id="67f85-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="67f85-147">0x10</span><span class="sxs-lookup"><span data-stu-id="67f85-147">0x10</span></span> | <span data-ttu-id="67f85-148">Ignoruje velikost písmen v porovnání řetězcových hodnot.</span><span class="sxs-lookup"><span data-stu-id="67f85-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="67f85-149">To platí pro řetězce a hodnoty kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="67f85-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="67f85-150">Porovnání názvů vlastností a kvalifikátorů je vždy rozlišovat velká a malá písmena bez ohledu na to, zda je tento příznak nastaven.</span><span class="sxs-lookup"><span data-stu-id="67f85-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="67f85-151">0x8</span><span class="sxs-lookup"><span data-stu-id="67f85-151">0x8</span></span> | <span data-ttu-id="67f85-152">Předpokládá, že porovnávané objekty jsou instancemi stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="67f85-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="67f85-153">Proto tento příznak porovnává pouze informace týkající se instancí.</span><span class="sxs-lookup"><span data-stu-id="67f85-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="67f85-154">Pomocí těchto příznaků Optimalizujte výkon.</span><span class="sxs-lookup"><span data-stu-id="67f85-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="67f85-155">Pokud objekty nejsou stejné třídy, výsledky nejsou definovány.</span><span class="sxs-lookup"><span data-stu-id="67f85-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="67f85-156">Můžete také zadat jeden složený příznak následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="67f85-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="67f85-157">Konstanta</span><span class="sxs-lookup"><span data-stu-id="67f85-157">Constant</span></span>  |<span data-ttu-id="67f85-158">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67f85-158">Value</span></span>  |<span data-ttu-id="67f85-159">Popis</span><span class="sxs-lookup"><span data-stu-id="67f85-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="67f85-160">0,8</span><span class="sxs-lookup"><span data-stu-id="67f85-160">0</span></span> | <span data-ttu-id="67f85-161">Zvažte všechny funkce v porovnání.</span><span class="sxs-lookup"><span data-stu-id="67f85-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="67f85-162">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67f85-162">Requirements</span></span>

<span data-ttu-id="67f85-163">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67f85-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="67f85-164">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="67f85-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="67f85-165">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67f85-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="67f85-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67f85-166">See also</span></span>

- [<span data-ttu-id="67f85-167">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="67f85-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
