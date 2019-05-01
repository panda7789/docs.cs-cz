---
title: Funkci Next (referenční dokumentace nespravovaného rozhraní API)
description: Další funkce načte další vlastnosti ve výčtu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 240544330fa352cbfdc01944e4be6bcad28dc96f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000217"
---
# <a name="next-function"></a><span data-ttu-id="27b59-103">Další funkce</span><span class="sxs-lookup"><span data-stu-id="27b59-103">Next function</span></span>
<span data-ttu-id="27b59-104">Načte další vlastnosti ve výčtu, která začíná volání [funkce BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="27b59-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="27b59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27b59-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="27b59-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="27b59-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="27b59-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="27b59-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="27b59-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="27b59-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="27b59-109">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="27b59-109">[in] Reserved.</span></span> <span data-ttu-id="27b59-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="27b59-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="27b59-111">[out] Nový `BSTR` , který obsahuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27b59-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="27b59-112">Tento parametr lze nastavit na `null` Pokud název není povinné.</span><span class="sxs-lookup"><span data-stu-id="27b59-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="27b59-113">[out] A `VARIANT` vyplněnou hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27b59-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="27b59-114">Tento parametr lze nastavit na `null` Pokud hodnota není povinné.</span><span class="sxs-lookup"><span data-stu-id="27b59-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="27b59-115">Pokud funkce vrátí chybový kód, `VARIANT` předán `pVal` je bez jakýchkoli úprav vlevo.</span><span class="sxs-lookup"><span data-stu-id="27b59-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="27b59-116">[out] Ukazatel `CIMTYPE` proměnné ( `LONG` do typ vlastnosti je umístěn).</span><span class="sxs-lookup"><span data-stu-id="27b59-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="27b59-117">Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je potřeba určit skutečný typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27b59-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="27b59-118">Tento parametr může být také `null`.</span><span class="sxs-lookup"><span data-stu-id="27b59-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="27b59-119">[out] `null`, nebo hodnotu, která obdrží informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27b59-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="27b59-120">Možné hodnoty v části [poznámky].</span><span class="sxs-lookup"><span data-stu-id="27b59-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="27b59-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27b59-121">Return value</span></span>

<span data-ttu-id="27b59-122">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="27b59-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="27b59-123">Konstanta</span><span class="sxs-lookup"><span data-stu-id="27b59-123">Constant</span></span>  |<span data-ttu-id="27b59-124">Value</span><span class="sxs-lookup"><span data-stu-id="27b59-124">Value</span></span>  |<span data-ttu-id="27b59-125">Popis</span><span class="sxs-lookup"><span data-stu-id="27b59-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="27b59-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="27b59-126">0x80041001</span></span> | <span data-ttu-id="27b59-127">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="27b59-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="27b59-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="27b59-128">0x80041008</span></span> | <span data-ttu-id="27b59-129">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="27b59-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="27b59-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="27b59-130">0x8004101d</span></span> | <span data-ttu-id="27b59-131">Došlo bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="27b59-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="27b59-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="27b59-132">0x80041006</span></span> | <span data-ttu-id="27b59-133">Nedostatek paměti je k dispozici zahájíte nový výčet.</span><span class="sxs-lookup"><span data-stu-id="27b59-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="27b59-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="27b59-134">0x80041015</span></span> | <span data-ttu-id="27b59-135">Volání vzdálených procedur mezi aktuálním procesem a službou Windows Management se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="27b59-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="27b59-136">0</span><span class="sxs-lookup"><span data-stu-id="27b59-136">0</span></span> | <span data-ttu-id="27b59-137">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="27b59-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="27b59-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="27b59-138">0x40005</span></span> | <span data-ttu-id="27b59-139">Nejsou žádné další vlastnosti ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="27b59-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="27b59-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27b59-140">Remarks</span></span>

<span data-ttu-id="27b59-141">Tato funkce zalamuje volání na [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) metody.</span><span class="sxs-lookup"><span data-stu-id="27b59-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="27b59-142">Tato metoda také vrátí hodnotu vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="27b59-142">This method also returns system properties.</span></span>

<span data-ttu-id="27b59-143">Pokud základní typ vlastnosti je cesta k objektu, datum nebo čas nebo jiné speciální typ, pak vrácený typ neobsahuje dostatek informací.</span><span class="sxs-lookup"><span data-stu-id="27b59-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="27b59-144">Volající musí zkontrolovat `CIMTYPE` zadané vlastnosti k určení, zda je odkaz na objekt, datum nebo čas nebo jiné speciální typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27b59-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="27b59-145">Pokud `plFlavor` není `null`, `LONG` hodnotu obdrží informace o původu vlastnost, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="27b59-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="27b59-146">Konstanta</span><span class="sxs-lookup"><span data-stu-id="27b59-146">Constant</span></span>  |<span data-ttu-id="27b59-147">Value</span><span class="sxs-lookup"><span data-stu-id="27b59-147">Value</span></span>  |<span data-ttu-id="27b59-148">Popis</span><span class="sxs-lookup"><span data-stu-id="27b59-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="27b59-149">0x40</span><span class="sxs-lookup"><span data-stu-id="27b59-149">0x40</span></span> | <span data-ttu-id="27b59-150">Vlastnost je standardní systém vlastnost.</span><span class="sxs-lookup"><span data-stu-id="27b59-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="27b59-151">0x20</span><span class="sxs-lookup"><span data-stu-id="27b59-151">0x20</span></span> | <span data-ttu-id="27b59-152">Pro třídu: Vlastnost se dědí z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="27b59-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="27b59-153">Pro instanci: Vlastnost, zatímco zděděná z nadřazené třídy nebyl změněn instancí.</span><span class="sxs-lookup"><span data-stu-id="27b59-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="27b59-154">0</span><span class="sxs-lookup"><span data-stu-id="27b59-154">0</span></span> | <span data-ttu-id="27b59-155">Pro třídu: Vlastnost patří k odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="27b59-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="27b59-156">Pro instanci: Instance; je změněna vlastnost To znamená, že byla zadána hodnota nebo kvalifikátor byla přidána nebo upravena.</span><span class="sxs-lookup"><span data-stu-id="27b59-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="27b59-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27b59-157">Requirements</span></span>

<span data-ttu-id="27b59-158">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b59-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="27b59-159">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="27b59-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="27b59-160">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27b59-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="27b59-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27b59-161">See also</span></span>

- [<span data-ttu-id="27b59-162">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="27b59-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)