---
title: Next – funkce (odkaz na nespravované rozhraní API)
description: Funkce Next načte další vlastnost ve výčtu.
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
ms.openlocfilehash: 95cea4cb3e7e7df2b6b52256a440b9a8d544f2db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798408"
---
# <a name="next-function"></a><span data-ttu-id="13890-103">Funkce Next</span><span class="sxs-lookup"><span data-stu-id="13890-103">Next function</span></span>
<span data-ttu-id="13890-104">Načte další vlastnost ve výčtu, který začíná voláním [funkce BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="13890-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="13890-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13890-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="13890-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13890-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="13890-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="13890-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="13890-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="13890-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="13890-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="13890-109">[in] Reserved.</span></span> <span data-ttu-id="13890-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="13890-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="13890-111">mimo Nový `BSTR` , který obsahuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="13890-112">Tento parametr můžete nastavit na, `null` Pokud není název vyžadován.</span><span class="sxs-lookup"><span data-stu-id="13890-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="13890-113">mimo `VARIANT` Vyplněný hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="13890-114">Tento parametr lze nastavit na `null` hodnotu, pokud není požadovaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="13890-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="13890-115">Pokud funkce vrátí kód chyby, `VARIANT` předané do `pVal` není ponecháno beze změny.</span><span class="sxs-lookup"><span data-stu-id="13890-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="13890-116">mimo Ukazatel na `CIMTYPE` proměnnou `LONG` (do které je umístěn typ vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="13890-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="13890-117">Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je nutné určit skutečný typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="13890-118">Tento parametr může být `null`také.</span><span class="sxs-lookup"><span data-stu-id="13890-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="13890-119">mimo `null`nebo hodnota, která přijímá informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="13890-120">Možné hodnoty jsou uvedeny v části [poznámky].</span><span class="sxs-lookup"><span data-stu-id="13890-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="13890-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13890-121">Return value</span></span>

<span data-ttu-id="13890-122">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="13890-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="13890-123">Konstanta</span><span class="sxs-lookup"><span data-stu-id="13890-123">Constant</span></span>  |<span data-ttu-id="13890-124">Value</span><span class="sxs-lookup"><span data-stu-id="13890-124">Value</span></span>  |<span data-ttu-id="13890-125">Popis</span><span class="sxs-lookup"><span data-stu-id="13890-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="13890-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="13890-126">0x80041001</span></span> | <span data-ttu-id="13890-127">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="13890-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="13890-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="13890-128">0x80041008</span></span> | <span data-ttu-id="13890-129">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="13890-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="13890-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="13890-130">0x8004101d</span></span> | <span data-ttu-id="13890-131">[`BeginEnumeration`](beginenumeration.md) Funkci se nevolalo.</span><span class="sxs-lookup"><span data-stu-id="13890-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="13890-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="13890-132">0x80041006</span></span> | <span data-ttu-id="13890-133">K zahájení nového výčtu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="13890-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="13890-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="13890-134">0x80041015</span></span> | <span data-ttu-id="13890-135">Vzdálené volání procedury mezi aktuálním procesem a správou systému Windows se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="13890-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="13890-136">0</span><span class="sxs-lookup"><span data-stu-id="13890-136">0</span></span> | <span data-ttu-id="13890-137">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="13890-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="13890-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="13890-138">0x40005</span></span> | <span data-ttu-id="13890-139">Ve výčtu nejsou žádné další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="13890-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13890-140">Remarks</span></span>

<span data-ttu-id="13890-141">Tato funkce zalomí volání metody [IWbemclassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .</span><span class="sxs-lookup"><span data-stu-id="13890-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="13890-142">Tato metoda také vrátí systémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="13890-142">This method also returns system properties.</span></span>

<span data-ttu-id="13890-143">Pokud podkladový typ vlastnosti je cesta objektu, datum nebo čas nebo jiný speciální typ, pak vrácený typ neobsahuje dostatek informací.</span><span class="sxs-lookup"><span data-stu-id="13890-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="13890-144">Volající musí prostudovat `CIMTYPE` pro zadanou vlastnost, aby určil, zda je vlastnost odkaz na objekt, datum nebo čas nebo jiný speciální typ.</span><span class="sxs-lookup"><span data-stu-id="13890-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="13890-145">Pokud `plFlavor` není,`LONG`hodnota obdrží informace o původu vlastnosti, a to následujícím způsobem: `null`</span><span class="sxs-lookup"><span data-stu-id="13890-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="13890-146">Konstanta</span><span class="sxs-lookup"><span data-stu-id="13890-146">Constant</span></span>  |<span data-ttu-id="13890-147">Value</span><span class="sxs-lookup"><span data-stu-id="13890-147">Value</span></span>  |<span data-ttu-id="13890-148">Popis</span><span class="sxs-lookup"><span data-stu-id="13890-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="13890-149">0x40</span><span class="sxs-lookup"><span data-stu-id="13890-149">0x40</span></span> | <span data-ttu-id="13890-150">Vlastnost je standardní systémová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="13890-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="13890-151">0x20</span><span class="sxs-lookup"><span data-stu-id="13890-151">0x20</span></span> | <span data-ttu-id="13890-152">Pro třídu: Vlastnost je zděděna z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="13890-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="13890-153">Pro instanci: Vlastnost, která byla zděděna z nadřazené třídy, nebyla upravena instancí.</span><span class="sxs-lookup"><span data-stu-id="13890-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="13890-154">0</span><span class="sxs-lookup"><span data-stu-id="13890-154">0</span></span> | <span data-ttu-id="13890-155">Pro třídu: Vlastnost patří do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="13890-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="13890-156">Pro instanci: Vlastnost je upravena instancí. To znamená, že byla zadána hodnota nebo byl přidán nebo upraven kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="13890-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="13890-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13890-157">Requirements</span></span>

<span data-ttu-id="13890-158">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13890-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="13890-159">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="13890-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="13890-160">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13890-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="13890-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13890-161">See also</span></span>

- [<span data-ttu-id="13890-162">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="13890-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
