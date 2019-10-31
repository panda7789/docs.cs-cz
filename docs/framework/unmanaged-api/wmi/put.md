---
title: Put – funkce (odkaz nespravovaného rozhraní API)
description: Funkce put přiřadí novou hodnotu pojmenované vlastnosti.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f1bb8aa09a269e3b8fd23f393d63a275d308a77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127407"
---
# <a name="put-function"></a><span data-ttu-id="00d36-103">Put – funkce</span><span class="sxs-lookup"><span data-stu-id="00d36-103">Put function</span></span>

<span data-ttu-id="00d36-104">Nastaví vlastnost s názvem na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="00d36-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="00d36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d36-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="00d36-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d36-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="00d36-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="00d36-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="00d36-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="00d36-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="00d36-109">pro Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-109">[in] The name of the property.</span></span> <span data-ttu-id="00d36-110">Tento parametr nelze `null`.</span><span class="sxs-lookup"><span data-stu-id="00d36-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="00d36-111">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="00d36-111">[in] Reserved.</span></span> <span data-ttu-id="00d36-112">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="00d36-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="00d36-113">pro Ukazatel na platný `VARIANT`, který se změní na novou hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="00d36-114">Pokud je `pVal` `null` nebo odkazuje na `VARIANT` typu `VT_NULL`, vlastnost je nastavena na hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="00d36-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="00d36-115">pro Typ `VARIANT` odkazoval na `pVal`.</span><span class="sxs-lookup"><span data-stu-id="00d36-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="00d36-116">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="00d36-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="00d36-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00d36-117">Return value</span></span>

<span data-ttu-id="00d36-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="00d36-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="00d36-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="00d36-119">Constant</span></span>  |<span data-ttu-id="00d36-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="00d36-120">Value</span></span>  |<span data-ttu-id="00d36-121">Popis</span><span class="sxs-lookup"><span data-stu-id="00d36-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="00d36-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="00d36-122">0x80041001</span></span> | <span data-ttu-id="00d36-123">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="00d36-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="00d36-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="00d36-124">0x80041008</span></span> | <span data-ttu-id="00d36-125">Jeden nebo více parametrů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="00d36-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="00d36-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="00d36-126">0x8004102a</span></span> | <span data-ttu-id="00d36-127">Typ vlastnosti nebyl rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="00d36-127">The property type is not recognized.</span></span> <span data-ttu-id="00d36-128">Tato hodnota je vrácena při vytváření instancí třídy, pokud třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="00d36-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="00d36-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="00d36-129">0x80041006</span></span> | <span data-ttu-id="00d36-130">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="00d36-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="00d36-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="00d36-131">0x80041005</span></span> | <span data-ttu-id="00d36-132">For Instances: označuje, že `pVal` odkazuje na `VARIANT` nesprávného typu pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="00d36-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="00d36-133">Pro definice tříd: vlastnost již v nadřazené třídě existuje a nový typ COM se liší od starého typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="00d36-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="00d36-134">0,8</span><span class="sxs-lookup"><span data-stu-id="00d36-134">0</span></span> | <span data-ttu-id="00d36-135">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="00d36-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="00d36-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00d36-136">Remarks</span></span>

<span data-ttu-id="00d36-137">Tato funkce zalomí volání metody [IWbemclassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="00d36-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="00d36-138">Tato funkce vždy přepíše aktuální hodnotu vlastnosti novou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="00d36-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="00d36-139">Pokud [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na definici třídy, `Put` vytvoří nebo aktualizuje hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="00d36-140">Když [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazuje na instanci CIM, `Put` aktualizuje pouze hodnotu vlastnosti. `Put` nemůže vytvořit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="00d36-141">Vlastnost System `__CLASS` je zapisovatelné pouze během vytváření třídy, pokud nemusí být ponechána prázdná.</span><span class="sxs-lookup"><span data-stu-id="00d36-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="00d36-142">Všechny ostatní vlastnosti systému jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="00d36-142">All other system properties are read-only.</span></span>

<span data-ttu-id="00d36-143">Uživatel nemůže vytvořit vlastnosti s názvy, které začínají nebo končí podtržítkem ("_").</span><span class="sxs-lookup"><span data-stu-id="00d36-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="00d36-144">Toto je vyhrazeno pro systémové třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="00d36-145">Pokud vlastnost nastavená funkcí `Put` existuje v nadřazené třídě, je výchozí hodnota vlastnosti změněna, pokud se typ vlastnosti neshoduje s typem nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="00d36-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="00d36-146">Pokud vlastnost neexistuje a nejedná se o neshodu typů, je vytvořena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="00d36-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="00d36-147">Parametr `vtType` použijte pouze při vytváření nových vlastností v definici třídy CIM a `pVal` je `null` nebo odkazuje na `VARIANT` typu `VT_NULL`.</span><span class="sxs-lookup"><span data-stu-id="00d36-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="00d36-148">V tomto případě parametr `vType` určuje typ CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="00d36-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="00d36-149">V každém případě `vtType` musí být 0.</span><span class="sxs-lookup"><span data-stu-id="00d36-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="00d36-150">`vtType` musí být také 0, pokud je podkladovým objektem instance (i když je `Val` `null`), protože typ vlastnosti je pevný a nelze jej změnit.</span><span class="sxs-lookup"><span data-stu-id="00d36-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="00d36-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="00d36-151">Example</span></span>

<span data-ttu-id="00d36-152">Příklad naleznete v metodě [IWbemclassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="00d36-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="00d36-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00d36-153">Requirements</span></span>

<span data-ttu-id="00d36-154">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d36-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="00d36-155">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="00d36-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="00d36-156">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="00d36-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="00d36-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00d36-157">See also</span></span>

- [<span data-ttu-id="00d36-158">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="00d36-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
