---
title: Get funkce (Unmanaged API Reference)
description: Funkce Get načte zadanou hodnotu vlastnosti.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174976"
---
# <a name="get-function"></a><span data-ttu-id="1bda5-103">Funkce Get</span><span class="sxs-lookup"><span data-stu-id="1bda5-103">Get function</span></span>

<span data-ttu-id="1bda5-104">Načte zadanou hodnotu vlastnosti, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="1bda5-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1bda5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bda5-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="1bda5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bda5-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1bda5-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="1bda5-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1bda5-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="1bda5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="1bda5-109">[v] Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1bda5-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="1bda5-110">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="1bda5-110">[in] Reserved.</span></span> <span data-ttu-id="1bda5-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="1bda5-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="1bda5-112">[out] Pokud funkce vrátí úspěšně, obsahuje hodnotu vlastnosti. `wszName`</span><span class="sxs-lookup"><span data-stu-id="1bda5-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="1bda5-113">Argumentu `pval` je přiřazen správný typ a hodnota kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="1bda5-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="1bda5-114">[out] Pokud funkce vrátí úspěšně, obsahuje [konstantu typu CIM,](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) která označuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1bda5-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="1bda5-115">Jeho hodnota může `null`být také .</span><span class="sxs-lookup"><span data-stu-id="1bda5-115">Its value can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="1bda5-116">[out] Pokud se funkce vrátí úspěšně, obdrží informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1bda5-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="1bda5-117">Jeho hodnota `null`může být , nebo jeden z následujících WBEM_FLAVOR_TYPE konstantdefinovaných v souboru hlavičky *WbemCli.h:*</span><span class="sxs-lookup"><span data-stu-id="1bda5-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span>

|<span data-ttu-id="1bda5-118">Trvalé</span><span class="sxs-lookup"><span data-stu-id="1bda5-118">Constant</span></span>  |<span data-ttu-id="1bda5-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1bda5-119">Value</span></span>  |<span data-ttu-id="1bda5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1bda5-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="1bda5-121">0x40</span><span class="sxs-lookup"><span data-stu-id="1bda5-121">0x40</span></span> | <span data-ttu-id="1bda5-122">Vlastnost je standardní systémová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1bda5-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="1bda5-123">0x20</span><span class="sxs-lookup"><span data-stu-id="1bda5-123">0x20</span></span> | <span data-ttu-id="1bda5-124">Pro třídu: Vlastnost je zděděna z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="1bda5-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="1bda5-125">Pro instanci: Vlastnost, zatímco zděděné z nadřazené třídy, nebyla změněna instance.</span><span class="sxs-lookup"><span data-stu-id="1bda5-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="1bda5-126">0</span><span class="sxs-lookup"><span data-stu-id="1bda5-126">0</span></span> | <span data-ttu-id="1bda5-127">Pro třídu: Vlastnost patří do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1bda5-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="1bda5-128">Pro instanci: Vlastnost je upravena instance; to znamená, že byla zadána hodnota nebo byl přidán nebo změněn kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="1bda5-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1bda5-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1bda5-129">Return value</span></span>

<span data-ttu-id="1bda5-130">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="1bda5-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1bda5-131">Trvalé</span><span class="sxs-lookup"><span data-stu-id="1bda5-131">Constant</span></span>  |<span data-ttu-id="1bda5-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1bda5-132">Value</span></span>  |<span data-ttu-id="1bda5-133">Popis</span><span class="sxs-lookup"><span data-stu-id="1bda5-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1bda5-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1bda5-134">0x80041001</span></span> | <span data-ttu-id="1bda5-135">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="1bda5-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1bda5-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1bda5-136">0x80041008</span></span> | <span data-ttu-id="1bda5-137">Jeden nebo více parametrů není platný.</span><span class="sxs-lookup"><span data-stu-id="1bda5-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1bda5-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1bda5-138">0x80041002</span></span> | <span data-ttu-id="1bda5-139">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="1bda5-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1bda5-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1bda5-140">0x80041006</span></span> | <span data-ttu-id="1bda5-141">K dokončení operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="1bda5-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1bda5-142">0</span><span class="sxs-lookup"><span data-stu-id="1bda5-142">0</span></span> | <span data-ttu-id="1bda5-143">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1bda5-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1bda5-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bda5-144">Remarks</span></span>

<span data-ttu-id="1bda5-145">Tato funkce zabalí volání [metody IWbemClassObject::Get.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)</span><span class="sxs-lookup"><span data-stu-id="1bda5-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="1bda5-146">Funkce `Get` může také vrátit vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="1bda5-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="1bda5-147">Argumentu `pVal` je přiřazen správný typ a hodnota pro kvalifikátor a funkci COM [VariantInit.](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)</span><span class="sxs-lookup"><span data-stu-id="1bda5-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="1bda5-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bda5-148">Requirements</span></span>

 <span data-ttu-id="1bda5-149">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bda5-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1bda5-150">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1bda5-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="1bda5-151">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1bda5-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1bda5-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bda5-152">See also</span></span>

- [<span data-ttu-id="1bda5-153">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="1bda5-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
