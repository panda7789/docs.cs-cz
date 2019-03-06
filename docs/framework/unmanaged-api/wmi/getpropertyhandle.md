---
title: Funkce GetPropertyHandle (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetPropertyHandle vrátí jedinečný popisovač identifikující vlastnosti.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92d48caf7de873850135c7410a5e4b5861131212
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366371"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="e2ec3-103">Funkce GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="e2ec3-103">GetPropertyHandle function</span></span>

<span data-ttu-id="e2ec3-104">Vrátí jedinečný popisovač identifikující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e2ec3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2ec3-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="e2ec3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2ec3-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e2ec3-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e2ec3-108">[in] Ukazatel [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="e2ec3-109">[in] Zakončený hodnotou null řetězec kódování UTF16 znaků, který obsahuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="e2ec3-110">[out] Ukazatel [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) člen výčtu, který představuje typ CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-110">[out] A pointer to a [`CIMTYPE`](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="e2ec3-111">[out] Ukazatel na celé číslo, které obsahuje popisovač vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="e2ec3-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2ec3-112">Return value</span></span>

<span data-ttu-id="e2ec3-113">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e2ec3-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e2ec3-114">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e2ec3-114">Constant</span></span>  |<span data-ttu-id="e2ec3-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e2ec3-115">Value</span></span>  |<span data-ttu-id="e2ec3-116">Popis</span><span class="sxs-lookup"><span data-stu-id="e2ec3-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e2ec3-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e2ec3-117">0x80041002</span></span> | <span data-ttu-id="e2ec3-118">Zadaný název vlastnosti nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e2ec3-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e2ec3-119">0x80041008</span></span> | <span data-ttu-id="e2ec3-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="e2ec3-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="e2ec3-121">0x8004100c</span></span> | <span data-ttu-id="e2ec3-122">Požadovaná vlastnost je typu jsou `CIM_OBJECT` nebo `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e2ec3-123">0</span><span class="sxs-lookup"><span data-stu-id="e2ec3-123">0</span></span> | <span data-ttu-id="e2ec3-124">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e2ec3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2ec3-125">Remarks</span></span>

<span data-ttu-id="e2ec3-126">Tato funkce zalamuje volání na [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) metody.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="e2ec3-127">Pomocí tohoto úchytu můžete identifikovat vlastnosti při použití [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) metody pro čtení nebo zápis hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="e2ec3-128">Obslužné rutiny mohou být získána pro vlastnosti všech datových typů jiných než `CIM_OBJECT` a `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="e2ec3-129">Vrátí popisovače práce napříč všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="e2ec3-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2ec3-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2ec3-130">Requirements</span></span>

<span data-ttu-id="e2ec3-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2ec3-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e2ec3-132">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e2ec3-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e2ec3-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ec3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e2ec3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2ec3-134">See also</span></span>

- [<span data-ttu-id="e2ec3-135">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e2ec3-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)