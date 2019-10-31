---
title: Funkce BeginEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce funkce BeginEnumeration resetuje enumerátor na začátek výčtu.
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
ms.openlocfilehash: 9e467234a45ae702a5b77a5f0fa8b75d4ff03c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124135"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="1a16e-103">Funkce BeginEnumeration</span><span class="sxs-lookup"><span data-stu-id="1a16e-103">BeginEnumeration function</span></span>
<span data-ttu-id="1a16e-104">Obnoví enumerátor zpět na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="1a16e-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1a16e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a16e-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="1a16e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a16e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1a16e-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="1a16e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1a16e-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="1a16e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="1a16e-109">pro Bitová kombinace příznaků nebo hodnot popsaných v oddílu [poznámky](#remarks) , které řídí vlastnosti zahrnuté ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="1a16e-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="1a16e-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-110">Return value</span></span>

<span data-ttu-id="1a16e-111">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="1a16e-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1a16e-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1a16e-112">Constant</span></span>  |<span data-ttu-id="1a16e-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-113">Value</span></span>  |<span data-ttu-id="1a16e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1a16e-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1a16e-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1a16e-115">0x80041008</span></span> | <span data-ttu-id="1a16e-116">Kombinace příznaků v `lEnumFlags` je neplatná nebo byl zadán neplatný argument.</span><span class="sxs-lookup"><span data-stu-id="1a16e-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="1a16e-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="1a16e-117">0x8004101d</span></span> | <span data-ttu-id="1a16e-118">Druhé volání `BeginEnumeration` bylo provedeno bez navýšení volání [`EndEnumeration`](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1a16e-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1a16e-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1a16e-119">0x80041006</span></span> | <span data-ttu-id="1a16e-120">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="1a16e-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1a16e-121">0,8</span><span class="sxs-lookup"><span data-stu-id="1a16e-121">0</span></span> | <span data-ttu-id="1a16e-122">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1a16e-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1a16e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a16e-123">Remarks</span></span>

<span data-ttu-id="1a16e-124">Tato funkce zalomí volání metody [IWbemclassObject:: funkce BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="1a16e-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="1a16e-125">Příznaky, které mohou být předány jako argument `lEnumFlags`, jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="1a16e-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="1a16e-126">Můžete zkombinovat jeden příznak z každé skupiny s libovolným příznakem z jakékoli jiné skupiny.</span><span class="sxs-lookup"><span data-stu-id="1a16e-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="1a16e-127">Příznaky ze stejné skupiny se však vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="1a16e-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="1a16e-128">**Skupina 1**</span><span class="sxs-lookup"><span data-stu-id="1a16e-128">**Group 1**</span></span>

|<span data-ttu-id="1a16e-129">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1a16e-129">Constant</span></span>  |<span data-ttu-id="1a16e-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-130">Value</span></span>  |<span data-ttu-id="1a16e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="1a16e-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="1a16e-132">0x4</span><span class="sxs-lookup"><span data-stu-id="1a16e-132">0x4</span></span> | <span data-ttu-id="1a16e-133">Zahrňte pouze vlastnosti, které tvoří klíč.</span><span class="sxs-lookup"><span data-stu-id="1a16e-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="1a16e-134">0x8</span><span class="sxs-lookup"><span data-stu-id="1a16e-134">0x8</span></span> | <span data-ttu-id="1a16e-135">Zahrnout vlastnosti, které jsou pouze odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="1a16e-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="1a16e-136">**Skupina 2**</span><span class="sxs-lookup"><span data-stu-id="1a16e-136">**Group 2**</span></span>

<span data-ttu-id="1a16e-137">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1a16e-137">Constant</span></span>  |<span data-ttu-id="1a16e-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-138">Value</span></span>  |<span data-ttu-id="1a16e-139">Popis</span><span class="sxs-lookup"><span data-stu-id="1a16e-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="1a16e-140">0x30</span><span class="sxs-lookup"><span data-stu-id="1a16e-140">0x30</span></span> | <span data-ttu-id="1a16e-141">Omezte výčet jenom na systémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a16e-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="1a16e-142">0x40</span><span class="sxs-lookup"><span data-stu-id="1a16e-142">0x40</span></span> | <span data-ttu-id="1a16e-143">Zahrnutí místních a rozšířících vlastností, ale vyloučení systémových vlastností z výčtu.</span><span class="sxs-lookup"><span data-stu-id="1a16e-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="1a16e-144">Pro třídy:</span><span class="sxs-lookup"><span data-stu-id="1a16e-144">For classes:</span></span>

<span data-ttu-id="1a16e-145">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1a16e-145">Constant</span></span>  |<span data-ttu-id="1a16e-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-146">Value</span></span>  |<span data-ttu-id="1a16e-147">Popis</span><span class="sxs-lookup"><span data-stu-id="1a16e-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="1a16e-148">0x100</span><span class="sxs-lookup"><span data-stu-id="1a16e-148">0x100</span></span> | <span data-ttu-id="1a16e-149">Omezte výčet na vlastnosti přepsané v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="1a16e-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="1a16e-150">0x100</span><span class="sxs-lookup"><span data-stu-id="1a16e-150">0x100</span></span> | <span data-ttu-id="1a16e-151">Omezte výčet na vlastnosti přepsané v aktuální definici třídy a na nové vlastnosti definované ve třídě.</span><span class="sxs-lookup"><span data-stu-id="1a16e-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="1a16e-152">0x300</span><span class="sxs-lookup"><span data-stu-id="1a16e-152">0x300</span></span> | <span data-ttu-id="1a16e-153">Maska (nikoli příznak), která se má použít u `lEnumFlags` hodnoty, aby zkontrolovala, jestli je nastavená možnost `WBEM_FLAG_CLASS_OVERRIDES_ONLY` nebo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`.</span><span class="sxs-lookup"><span data-stu-id="1a16e-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1a16e-154">0x10</span><span class="sxs-lookup"><span data-stu-id="1a16e-154">0x10</span></span> | <span data-ttu-id="1a16e-155">Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné.</span><span class="sxs-lookup"><span data-stu-id="1a16e-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="1a16e-156">0x20</span><span class="sxs-lookup"><span data-stu-id="1a16e-156">0x20</span></span> | <span data-ttu-id="1a16e-157">Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="1a16e-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="1a16e-158">Instance:</span><span class="sxs-lookup"><span data-stu-id="1a16e-158">For instances:</span></span>

<span data-ttu-id="1a16e-159">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1a16e-159">Constant</span></span>  |<span data-ttu-id="1a16e-160">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1a16e-160">Value</span></span>  |<span data-ttu-id="1a16e-161">Popis</span><span class="sxs-lookup"><span data-stu-id="1a16e-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="1a16e-162">0x10</span><span class="sxs-lookup"><span data-stu-id="1a16e-162">0x10</span></span> | <span data-ttu-id="1a16e-163">Omezte výčet na vlastnosti, které jsou definovány nebo změněny ve třídě samotné.</span><span class="sxs-lookup"><span data-stu-id="1a16e-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="1a16e-164">0x20</span><span class="sxs-lookup"><span data-stu-id="1a16e-164">0x20</span></span> | <span data-ttu-id="1a16e-165">Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="1a16e-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="1a16e-166">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a16e-166">Requirements</span></span>  
 <span data-ttu-id="1a16e-167">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a16e-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a16e-168">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="1a16e-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1a16e-169">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1a16e-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a16e-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a16e-170">See also</span></span>

- [<span data-ttu-id="1a16e-171">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="1a16e-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
