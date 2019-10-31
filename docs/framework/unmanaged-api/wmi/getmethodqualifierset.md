---
title: GetMethodQualifierSet – funkce (Reference nespravovaného rozhraní API)
description: Funkce GetMethodQualifierSet načte kvalifikátor sady metody.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1a36200fd214d013a10ed21c22e1f652de2cbf17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102578"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="97037-103">Funkce GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="97037-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="97037-104">Načte kvalifikátor sady pro konkrétní metodu.</span><span class="sxs-lookup"><span data-stu-id="97037-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="97037-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97037-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="97037-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97037-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="97037-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="97037-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="97037-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="97037-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="97037-109">pro Název metody.</span><span class="sxs-lookup"><span data-stu-id="97037-109">[in] The method  name.</span></span> <span data-ttu-id="97037-110">`wszMethod` musí ukazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="97037-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="97037-111">mimo Přijímá ukazatel rozhraní, který umožňuje přístup k kvalifikátorům metody.</span><span class="sxs-lookup"><span data-stu-id="97037-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="97037-112">`ppQualSet` nelze `null`.</span><span class="sxs-lookup"><span data-stu-id="97037-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="97037-113">Pokud dojde k chybě, nový objekt se nevrátí a ukazatel je nastaven tak, aby odkazoval na `null`.</span><span class="sxs-lookup"><span data-stu-id="97037-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="97037-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97037-114">Return value</span></span>

<span data-ttu-id="97037-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="97037-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="97037-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="97037-116">Constant</span></span>  |<span data-ttu-id="97037-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="97037-117">Value</span></span>  |<span data-ttu-id="97037-118">Popis</span><span class="sxs-lookup"><span data-stu-id="97037-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="97037-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="97037-119">0x80041002</span></span> | <span data-ttu-id="97037-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="97037-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="97037-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="97037-121">0x80041008</span></span> | <span data-ttu-id="97037-122">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="97037-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="97037-123">0,8</span><span class="sxs-lookup"><span data-stu-id="97037-123">0</span></span> | <span data-ttu-id="97037-124">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="97037-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="97037-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97037-125">Remarks</span></span>

<span data-ttu-id="97037-126">Tato funkce zalomí volání metody [IWbemclassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="97037-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="97037-127">Volání této funkce je podporováno pouze v případě, že aktuální objekt je definice třídy modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="97037-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="97037-128">Manipulace s metodou není k dispozici pro ukazatele [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="97037-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="97037-129">Vzhledem k tomu, že každá metoda může mít své vlastní kvalifikátory, [ukazatel IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit tyto kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="97037-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="97037-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97037-130">Requirements</span></span>

<span data-ttu-id="97037-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97037-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="97037-132">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="97037-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="97037-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="97037-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="97037-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97037-134">See also</span></span>

- [<span data-ttu-id="97037-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="97037-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
