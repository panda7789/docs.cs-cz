---
title: GetPropertyOrigin – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetPropertyOrigin určuje třídu, ve které je deklarována vlastnost.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6cab3765f0359f5dd18831acaaa1aefce3fe1081
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101854"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="a1064-103">Funkce GetPropertyOrigin</span><span class="sxs-lookup"><span data-stu-id="a1064-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="a1064-104">Určuje třídu, ve které je deklarována vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1064-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a1064-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1064-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="a1064-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1064-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a1064-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a1064-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a1064-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a1064-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="a1064-109">pro Název vlastnosti pro objekt, jehož vlastnící třída je požadována.</span><span class="sxs-lookup"><span data-stu-id="a1064-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="a1064-110">mimo Přijímá název třídy, která vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1064-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="a1064-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a1064-111">Return value</span></span>

<span data-ttu-id="a1064-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a1064-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a1064-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a1064-113">Constant</span></span>  |<span data-ttu-id="a1064-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1064-114">Value</span></span>  |<span data-ttu-id="a1064-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a1064-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a1064-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a1064-116">0x80041001</span></span> | <span data-ttu-id="a1064-117">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="a1064-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a1064-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a1064-118">0x80041002</span></span> | <span data-ttu-id="a1064-119">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="a1064-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a1064-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a1064-120">0x80041008</span></span> | <span data-ttu-id="a1064-121">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="a1064-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a1064-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a1064-122">0x80041006</span></span> | <span data-ttu-id="a1064-123">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="a1064-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a1064-124">0,8</span><span class="sxs-lookup"><span data-stu-id="a1064-124">0</span></span> | <span data-ttu-id="a1064-125">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a1064-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a1064-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1064-126">Remarks</span></span>

<span data-ttu-id="a1064-127">Tato funkce zalomí volání metody [IWbemclassObject:: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) .</span><span class="sxs-lookup"><span data-stu-id="a1064-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="a1064-128">Vzhledem k tomu, že třída může dědit vlastnosti z jedné nebo více základních tříd, vývojáři často chtějí určit vlastnost, ve které je daná metoda definována.</span><span class="sxs-lookup"><span data-stu-id="a1064-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="a1064-129">Parametr `pstrClassName` nesmí nasměrovat na platný `BSTR` před voláním funkce, protože se jedná o parametr `out`; Tento ukazatel se nevrátí po vrácení funkce.</span><span class="sxs-lookup"><span data-stu-id="a1064-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1064-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1064-130">Requirements</span></span>

<span data-ttu-id="a1064-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1064-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a1064-132">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="a1064-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a1064-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a1064-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a1064-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1064-134">See also</span></span>

- [<span data-ttu-id="a1064-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a1064-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
