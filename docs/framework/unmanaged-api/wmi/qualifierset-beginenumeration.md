---
title: QualifierSet_BeginEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_BeginEnumeration obnoví enumerátor kvalifikátorů objektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798343"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="72dd1-103">QualifierSet_BeginEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="72dd1-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="72dd1-104">Obnoví enumerátor kvalifikátorů objektu na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="72dd1-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="72dd1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72dd1-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="72dd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="72dd1-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="72dd1-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="72dd1-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="72dd1-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="72dd1-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="72dd1-109">pro Bitová kombinace příznaků nebo hodnot popsaných v části [poznámky](#remarks) , které určují kvalifikátory, které mají být zahrnuty do výčtu.</span><span class="sxs-lookup"><span data-stu-id="72dd1-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="72dd1-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="72dd1-110">Return value</span></span>

<span data-ttu-id="72dd1-111">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="72dd1-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="72dd1-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="72dd1-112">Constant</span></span>  |<span data-ttu-id="72dd1-113">Value</span><span class="sxs-lookup"><span data-stu-id="72dd1-113">Value</span></span>  |<span data-ttu-id="72dd1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="72dd1-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="72dd1-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="72dd1-115">0x80041008</span></span> | <span data-ttu-id="72dd1-116">`lFlags` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="72dd1-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="72dd1-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="72dd1-117">0x8004101d</span></span> | <span data-ttu-id="72dd1-118">Druhé volání `QualifierSet_BeginEnumeration` bylo provedeno bez navýšení [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)volání.</span><span class="sxs-lookup"><span data-stu-id="72dd1-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="72dd1-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="72dd1-119">0x80041006</span></span> | <span data-ttu-id="72dd1-120">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="72dd1-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="72dd1-121">0</span><span class="sxs-lookup"><span data-stu-id="72dd1-121">0</span></span> | <span data-ttu-id="72dd1-122">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="72dd1-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="72dd1-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72dd1-123">Remarks</span></span>

<span data-ttu-id="72dd1-124">Tato funkce zalomí volání metody [IWbemQualifierSet:: funkce BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .</span><span class="sxs-lookup"><span data-stu-id="72dd1-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="72dd1-125">Chcete-li vytvořit výčet všech kvalifikátorů objektu, musí být tato metoda volána před prvním voláním [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="72dd1-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="72dd1-126">Pořadí, ve kterém jsou kvalifikátory výčty, je zaručené pro daný výčet jako invariantní.</span><span class="sxs-lookup"><span data-stu-id="72dd1-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="72dd1-127">Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v souboru hlaviček *WbemCli. h* , nebo je můžete v kódu definovat jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="72dd1-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="72dd1-128">Konstanta</span><span class="sxs-lookup"><span data-stu-id="72dd1-128">Constant</span></span>  |<span data-ttu-id="72dd1-129">Value</span><span class="sxs-lookup"><span data-stu-id="72dd1-129">Value</span></span>  |<span data-ttu-id="72dd1-130">Popis</span><span class="sxs-lookup"><span data-stu-id="72dd1-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="72dd1-131">0</span><span class="sxs-lookup"><span data-stu-id="72dd1-131">0</span></span> | <span data-ttu-id="72dd1-132">Vrátí názvy všech kvalifikátorů.</span><span class="sxs-lookup"><span data-stu-id="72dd1-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="72dd1-133">0x10</span><span class="sxs-lookup"><span data-stu-id="72dd1-133">0x10</span></span> | <span data-ttu-id="72dd1-134">Vrátí pouze názvy kvalifikátorů specifických pro aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="72dd1-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="72dd1-135">Pro vlastnost: Vrátí pouze kvalifikátory specifické pro vlastnost (včetně přepsání), a ne tyto kvalifikátory šířené z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="72dd1-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="72dd1-136">Pro instanci: Vrátí pouze názvy kvalifikátorů specifických pro instanci.</span><span class="sxs-lookup"><span data-stu-id="72dd1-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="72dd1-137">Pro třídu: Vrátí pouze kvalifikátory specifické pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="72dd1-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="72dd1-138">0x20</span><span class="sxs-lookup"><span data-stu-id="72dd1-138">0x20</span></span> | <span data-ttu-id="72dd1-139">Vrátí pouze názvy kvalifikátorů šířených z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="72dd1-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="72dd1-140">Pro vlastnost: Vrátí pouze kvalifikátory šířené do této vlastnosti z definice třídy, nikoli z samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="72dd1-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="72dd1-141">Pro instanci: Vrátí pouze ty kvalifikátory šířené z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="72dd1-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="72dd1-142">Pro třídu: Vrátí pouze ty názvy kvalifikátorů zděděné z nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="72dd1-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="72dd1-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72dd1-143">Requirements</span></span>

<span data-ttu-id="72dd1-144">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72dd1-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="72dd1-145">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="72dd1-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="72dd1-146">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="72dd1-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="72dd1-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72dd1-147">See also</span></span>

- [<span data-ttu-id="72dd1-148">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="72dd1-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
