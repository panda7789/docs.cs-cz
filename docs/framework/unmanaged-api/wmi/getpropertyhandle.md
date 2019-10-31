---
title: GetPropertyHandle – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetPropertyHandle vrací jedinečný popisovač, který identifikuje vlastnost.
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
ms.openlocfilehash: 5af003f0295e0b403727f9af6b03ab81c4b8bccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101860"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="cad0a-103">Funkce GetPropertyHandle</span><span class="sxs-lookup"><span data-stu-id="cad0a-103">GetPropertyHandle function</span></span>

<span data-ttu-id="cad0a-104">Vrací jedinečný popisovač, který identifikuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cad0a-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="cad0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cad0a-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="cad0a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cad0a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="cad0a-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="cad0a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="cad0a-108">pro Ukazatel na instanci [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .</span><span class="sxs-lookup"><span data-stu-id="cad0a-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="cad0a-109">pro Řetězec zakončený znakem null UTF16 znaků, který obsahuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cad0a-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="cad0a-110">mimo Ukazatel na [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) člen výčtu, který představuje typ CIM vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cad0a-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="cad0a-111">mimo Ukazatel na celé číslo, které obsahuje popisovač vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cad0a-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="cad0a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cad0a-112">Return value</span></span>

<span data-ttu-id="cad0a-113">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="cad0a-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cad0a-114">Konstanta</span><span class="sxs-lookup"><span data-stu-id="cad0a-114">Constant</span></span>  |<span data-ttu-id="cad0a-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cad0a-115">Value</span></span>  |<span data-ttu-id="cad0a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cad0a-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="cad0a-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="cad0a-117">0x80041002</span></span> | <span data-ttu-id="cad0a-118">Zadaný název vlastnosti nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="cad0a-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cad0a-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cad0a-119">0x80041008</span></span> | <span data-ttu-id="cad0a-120">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="cad0a-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="cad0a-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="cad0a-121">0x8004100c</span></span> | <span data-ttu-id="cad0a-122">Požadovaná vlastnost je typu `CIM_OBJECT` nebo `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="cad0a-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cad0a-123">0,8</span><span class="sxs-lookup"><span data-stu-id="cad0a-123">0</span></span> | <span data-ttu-id="cad0a-124">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="cad0a-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="cad0a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cad0a-125">Remarks</span></span>

<span data-ttu-id="cad0a-126">Tato funkce zalomí volání metody [IWbemclassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .</span><span class="sxs-lookup"><span data-stu-id="cad0a-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="cad0a-127">Tento popisovač můžete použít k identifikaci vlastností při použití metod [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) ke čtení nebo zápisu hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="cad0a-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="cad0a-128">Obslužné rutiny lze načíst pro vlastnosti všech datových typů kromě `CIM_OBJECT` a `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="cad0a-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="cad0a-129">Vrácené obslužné rutiny fungují napříč všemi instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="cad0a-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="cad0a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cad0a-130">Requirements</span></span>

<span data-ttu-id="cad0a-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad0a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cad0a-132">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="cad0a-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="cad0a-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cad0a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cad0a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cad0a-134">See also</span></span>

- [<span data-ttu-id="cad0a-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="cad0a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
