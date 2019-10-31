---
title: GetPropertyQualifierSet – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetPropertyQualifierSet načte kvalifikátor sady pro vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127459"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="ec360-103">GetPropertyQualifierSet – funkce</span><span class="sxs-lookup"><span data-stu-id="ec360-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="ec360-104">Načte kvalifikátor sady pro konkrétní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ec360-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ec360-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec360-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="ec360-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec360-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ec360-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ec360-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ec360-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ec360-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="ec360-109">pro Název vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ec360-109">[in] The property  name.</span></span> <span data-ttu-id="ec360-110">`wszProperty` musí ukazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="ec360-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="ec360-111">mimo Přijímá ukazatel rozhraní, který umožňuje přístup k kvalifikátorům vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ec360-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="ec360-112">`ppQualSet` nelze `null`.</span><span class="sxs-lookup"><span data-stu-id="ec360-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="ec360-113">Pokud dojde k chybě, nový objekt se nevrátí a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="ec360-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec360-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ec360-114">Return value</span></span>

<span data-ttu-id="ec360-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ec360-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ec360-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ec360-116">Constant</span></span>  |<span data-ttu-id="ec360-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec360-117">Value</span></span>  |<span data-ttu-id="ec360-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ec360-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ec360-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ec360-119">0x80041001</span></span> | <span data-ttu-id="ec360-120">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="ec360-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="ec360-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ec360-121">0x80041002</span></span> | <span data-ttu-id="ec360-122">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ec360-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ec360-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ec360-123">0x80041006</span></span> | <span data-ttu-id="ec360-124">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ec360-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ec360-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ec360-125">0x80041008</span></span> | <span data-ttu-id="ec360-126">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="ec360-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="ec360-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="ec360-127">0x80041030</span></span> | <span data-ttu-id="ec360-128">Funkce se pokusí získat kvalifikátory systémové vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ec360-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ec360-129">0,8</span><span class="sxs-lookup"><span data-stu-id="ec360-129">0</span></span> | <span data-ttu-id="ec360-130">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ec360-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ec360-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec360-131">Remarks</span></span>

<span data-ttu-id="ec360-132">Tato funkce zalomí volání metody [IWbemclassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="ec360-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="ec360-133">Volání této funkce je podporováno pouze v případě, že aktuální objekt je definice třídy modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="ec360-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="ec360-134">Manipulace s metodou není k dispozici pro ukazatele [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="ec360-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="ec360-135">Vzhledem k tomu, že každá metoda může mít své vlastní kvalifikátory, [ukazatel IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit tyto kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="ec360-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="ec360-136">Vzhledem k tomu, že systémové vlastnosti nemají žádné kvalifikátory, funkce vrátí `WBEM_E_SYSTEM_PROPERTY`, pokud se pokusíte získat ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pro vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="ec360-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec360-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec360-137">Requirements</span></span>

<span data-ttu-id="ec360-138">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec360-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ec360-139">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ec360-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ec360-140">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ec360-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ec360-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec360-141">See also</span></span>

- [<span data-ttu-id="ec360-142">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ec360-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
