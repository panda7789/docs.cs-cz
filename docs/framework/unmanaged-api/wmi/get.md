---
title: Get – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 60f29b91000fd3c07efea88dcc319eb283a4af78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120328"
---
# <a name="get-function"></a><span data-ttu-id="37f13-103">Funkce Get</span><span class="sxs-lookup"><span data-stu-id="37f13-103">Get function</span></span>

<span data-ttu-id="37f13-104">Načte zadanou hodnotu vlastnosti, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="37f13-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="37f13-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37f13-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="37f13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37f13-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="37f13-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="37f13-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="37f13-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="37f13-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="37f13-109">pro Název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37f13-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="37f13-110">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="37f13-110">[in] Reserved.</span></span> <span data-ttu-id="37f13-111">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="37f13-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="37f13-112">mimo Pokud se funkce vrátí úspěšně, obsahuje hodnotu vlastnosti `wszName`.</span><span class="sxs-lookup"><span data-stu-id="37f13-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="37f13-113">Argumentu `pval` je přiřazen správný typ a hodnota kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="37f13-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="37f13-114">mimo Pokud se funkce vrátí úspěšně, obsahuje [konstantu typu CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) , která označuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37f13-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="37f13-115">Její hodnota může být také `null`.</span><span class="sxs-lookup"><span data-stu-id="37f13-115">Its value can also be `null`.</span></span> 

`plFlavor`\
<span data-ttu-id="37f13-116">mimo Pokud se funkce vrátí úspěšně, obdrží informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37f13-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="37f13-117">Jeho hodnota může být `null`nebo jedna z následujících konstant WBEM_FLAVOR_TYPE definovaných v souboru hlaviček *WbemCli. h* :</span><span class="sxs-lookup"><span data-stu-id="37f13-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span> 

|<span data-ttu-id="37f13-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="37f13-118">Constant</span></span>  |<span data-ttu-id="37f13-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37f13-119">Value</span></span>  |<span data-ttu-id="37f13-120">Popis</span><span class="sxs-lookup"><span data-stu-id="37f13-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="37f13-121">0x40</span><span class="sxs-lookup"><span data-stu-id="37f13-121">0x40</span></span> | <span data-ttu-id="37f13-122">Vlastnost je standardní systémová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="37f13-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="37f13-123">0x20</span><span class="sxs-lookup"><span data-stu-id="37f13-123">0x20</span></span> | <span data-ttu-id="37f13-124">Pro třídu: vlastnost je zděděna z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="37f13-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="37f13-125">Pro instanci: vlastnost, která byla zděděna z nadřazené třídy, nebyla upravena instancí.</span><span class="sxs-lookup"><span data-stu-id="37f13-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="37f13-126">0,8</span><span class="sxs-lookup"><span data-stu-id="37f13-126">0</span></span> | <span data-ttu-id="37f13-127">Pro třídu: vlastnost patří do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="37f13-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="37f13-128">Pro instanci: vlastnost je upravena instancí. To znamená, že byla zadána hodnota nebo byl přidán nebo upraven kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="37f13-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="37f13-129">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37f13-129">Return value</span></span>

<span data-ttu-id="37f13-130">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="37f13-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="37f13-131">Konstanta</span><span class="sxs-lookup"><span data-stu-id="37f13-131">Constant</span></span>  |<span data-ttu-id="37f13-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37f13-132">Value</span></span>  |<span data-ttu-id="37f13-133">Popis</span><span class="sxs-lookup"><span data-stu-id="37f13-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="37f13-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="37f13-134">0x80041001</span></span> | <span data-ttu-id="37f13-135">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="37f13-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="37f13-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="37f13-136">0x80041008</span></span> | <span data-ttu-id="37f13-137">Jeden nebo více parametrů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="37f13-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="37f13-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="37f13-138">0x80041002</span></span> | <span data-ttu-id="37f13-139">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="37f13-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="37f13-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="37f13-140">0x80041006</span></span> | <span data-ttu-id="37f13-141">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="37f13-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="37f13-142">0,8</span><span class="sxs-lookup"><span data-stu-id="37f13-142">0</span></span> | <span data-ttu-id="37f13-143">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="37f13-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="37f13-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37f13-144">Remarks</span></span>

<span data-ttu-id="37f13-145">Tato funkce zalomí volání metody [IWbemclassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .</span><span class="sxs-lookup"><span data-stu-id="37f13-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="37f13-146">Funkce `Get` může také vracet systémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37f13-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="37f13-147">Argumentu `pVal` je přiřazen správný typ a hodnota kvalifikátoru a funkce [VARIANTINIT](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) com.</span><span class="sxs-lookup"><span data-stu-id="37f13-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="37f13-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37f13-148">Requirements</span></span>

 <span data-ttu-id="37f13-149">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f13-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="37f13-150">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="37f13-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="37f13-151">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37f13-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="37f13-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37f13-152">See also</span></span>

- [<span data-ttu-id="37f13-153">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="37f13-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
