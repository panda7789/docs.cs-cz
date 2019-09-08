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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798526"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="1c67c-103">Funkce GetMethodQualifierSet</span><span class="sxs-lookup"><span data-stu-id="1c67c-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="1c67c-104">Načte kvalifikátor sady pro konkrétní metodu.</span><span class="sxs-lookup"><span data-stu-id="1c67c-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1c67c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c67c-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="1c67c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c67c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1c67c-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="1c67c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1c67c-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="1c67c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="1c67c-109">pro Název metody.</span><span class="sxs-lookup"><span data-stu-id="1c67c-109">[in] The method  name.</span></span> <span data-ttu-id="1c67c-110">`wszMethod`musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="1c67c-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="1c67c-111">mimo Přijímá ukazatel rozhraní, který umožňuje přístup k kvalifikátorům metody.</span><span class="sxs-lookup"><span data-stu-id="1c67c-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="1c67c-112">`ppQualSet`nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="1c67c-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="1c67c-113">Pokud dojde k chybě, nový objekt se nevrátí a ukazatel je nastaven na hodnotu Point `null`.</span><span class="sxs-lookup"><span data-stu-id="1c67c-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="1c67c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1c67c-114">Return value</span></span>

<span data-ttu-id="1c67c-115">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="1c67c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1c67c-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1c67c-116">Constant</span></span>  |<span data-ttu-id="1c67c-117">Value</span><span class="sxs-lookup"><span data-stu-id="1c67c-117">Value</span></span>  |<span data-ttu-id="1c67c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1c67c-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1c67c-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1c67c-119">0x80041002</span></span> | <span data-ttu-id="1c67c-120">Zadaná metoda neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1c67c-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1c67c-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1c67c-121">0x80041008</span></span> | <span data-ttu-id="1c67c-122">Parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="1c67c-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1c67c-123">0</span><span class="sxs-lookup"><span data-stu-id="1c67c-123">0</span></span> | <span data-ttu-id="1c67c-124">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1c67c-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1c67c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c67c-125">Remarks</span></span>

<span data-ttu-id="1c67c-126">Tato funkce zalomí volání metody [IWbemclassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="1c67c-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="1c67c-127">Volání této funkce je podporováno pouze v případě, že aktuální objekt je definice třídy modelu CIM.</span><span class="sxs-lookup"><span data-stu-id="1c67c-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="1c67c-128">Manipulace s metodou není k dispozici pro ukazatele [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="1c67c-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="1c67c-129">Vzhledem k tomu, že každá metoda může mít své vlastní kvalifikátory, [ukazatel IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umožňuje volajícímu přidat, upravit nebo odstranit tyto kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="1c67c-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c67c-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c67c-130">Requirements</span></span>

<span data-ttu-id="1c67c-131">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c67c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1c67c-132">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1c67c-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1c67c-133">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c67c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1c67c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c67c-134">See also</span></span>

- [<span data-ttu-id="1c67c-135">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="1c67c-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
