---
title: QualifierSet_GetNames – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_GetNames načítá názvy kvalifikátorů z objektu nebo vlastnosti.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141690"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="5a7cb-103">QualifierSet_GetNames – funkce</span><span class="sxs-lookup"><span data-stu-id="5a7cb-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="5a7cb-104">Načte názvy všech kvalifikátorů nebo určitých kvalifikátorů, které jsou k dispozici z aktuálního objektu nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5a7cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a7cb-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="5a7cb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a7cb-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="5a7cb-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="5a7cb-108">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="5a7cb-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="5a7cb-109">pro Jeden z následujících příznaků nebo hodnot, které určují názvy, které mají být zahrnuty do výčtu.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="5a7cb-110">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5a7cb-110">Constant</span></span>  |<span data-ttu-id="5a7cb-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a7cb-111">Value</span></span>  |<span data-ttu-id="5a7cb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5a7cb-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="5a7cb-113">0,8</span><span class="sxs-lookup"><span data-stu-id="5a7cb-113">0</span></span> | <span data-ttu-id="5a7cb-114">Vrátí názvy všech kvalifikátorů.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="5a7cb-115">0x10</span><span class="sxs-lookup"><span data-stu-id="5a7cb-115">0x10</span></span> | <span data-ttu-id="5a7cb-116">Vrátí pouze názvy kvalifikátorů specifických pro aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="5a7cb-117">Pro vlastnost: vrátí pouze kvalifikátory specifické pro vlastnost (včetně přepsání), a nikoli tyto kvalifikátory šířené z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5a7cb-118">Pro instanci: vracet pouze názvy kvalifikátorů specifických pro instanci.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="5a7cb-119">Pro třídu: vracet pouze kvalifikátory specifické pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="5a7cb-120">0x20</span><span class="sxs-lookup"><span data-stu-id="5a7cb-120">0x20</span></span> | <span data-ttu-id="5a7cb-121">Vrátí pouze názvy kvalifikátorů šířených z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="5a7cb-122">Pro vlastnost: vrátí pouze kvalifikátory šířené do této vlastnosti z definice třídy, nikoli z samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="5a7cb-123">Pro instanci: vrátí pouze ty kvalifikátory šířené z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="5a7cb-124">Pro třídu: vrátí pouze ty názvy kvalifikátorů zděděné z nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="5a7cb-125">mimo Nový `SAFEARRAY`, který obsahuje požadované názvy.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="5a7cb-126">Pole může mít 0 prvků.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-126">The array can have 0 elements.</span></span> <span data-ttu-id="5a7cb-127">Pokud dojde k chybě, nevrátí se nový `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a7cb-128">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a7cb-128">Return value</span></span>

<span data-ttu-id="5a7cb-129">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5a7cb-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5a7cb-130">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5a7cb-130">Constant</span></span>  |<span data-ttu-id="5a7cb-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a7cb-131">Value</span></span>  |<span data-ttu-id="5a7cb-132">Popis</span><span class="sxs-lookup"><span data-stu-id="5a7cb-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5a7cb-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5a7cb-133">0x80041008</span></span> | <span data-ttu-id="5a7cb-134">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5a7cb-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5a7cb-135">0x80041006</span></span> | <span data-ttu-id="5a7cb-136">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5a7cb-137">0,8</span><span class="sxs-lookup"><span data-stu-id="5a7cb-137">0</span></span> | <span data-ttu-id="5a7cb-138">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="5a7cb-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a7cb-139">Remarks</span></span>

<span data-ttu-id="5a7cb-140">Tato funkce zalomí volání metody [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .</span><span class="sxs-lookup"><span data-stu-id="5a7cb-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="5a7cb-141">Jakmile nazískáte názvy kvalifikátorů, můžete k jednotlivým kvalifikátorům přistupovat pomocí volání funkce [QualifierSet_Get](qualifierset-get.md) .</span><span class="sxs-lookup"><span data-stu-id="5a7cb-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="5a7cb-142">Nejedná se o chybu pro daný objekt, který má nulové kvalifikátory, takže počet řetězců v `pstrNames` při návratu může být 0, i když funkce vrací `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5a7cb-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a7cb-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a7cb-143">Requirements</span></span>

<span data-ttu-id="5a7cb-144">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a7cb-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5a7cb-145">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="5a7cb-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="5a7cb-146">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5a7cb-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5a7cb-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a7cb-147">See also</span></span>

- [<span data-ttu-id="5a7cb-148">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5a7cb-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
