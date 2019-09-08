---
title: GetMethod – funkce (nespravované reference rozhraní API)
description: Funkce GetMethod načte informace o metodě.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798564"
---
# <a name="getmethod-function"></a><span data-ttu-id="0111c-103">Funkce GetMethod</span><span class="sxs-lookup"><span data-stu-id="0111c-103">GetMethod function</span></span>

<span data-ttu-id="0111c-104">Načte informace o zadané metodě.</span><span class="sxs-lookup"><span data-stu-id="0111c-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0111c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0111c-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="0111c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0111c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="0111c-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="0111c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="0111c-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="0111c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="0111c-109">pro Název metody.</span><span class="sxs-lookup"><span data-stu-id="0111c-109">[in] The method name.</span></span> <span data-ttu-id="0111c-110">Tento parametr nemůže být `null` a musí odkazovat na platný. `LPCWSTR`</span><span class="sxs-lookup"><span data-stu-id="0111c-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="0111c-111">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="0111c-111">[in] Reserved.</span></span> <span data-ttu-id="0111c-112">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="0111c-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="0111c-113">mimo Ukazatel na adresu instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , která popisuje parametry v parametrech metody.</span><span class="sxs-lookup"><span data-stu-id="0111c-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="0111c-114">Tento parametr je ignorován, pokud je nastaven na `null`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0111c-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="0111c-115">mimo Ukazatel na adresu instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , která popisuje výstupní parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0111c-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="0111c-116">Tento parametr je ignorován, pokud je nastaven na `null`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0111c-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0111c-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0111c-117">Return value</span></span>

<span data-ttu-id="0111c-118">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="0111c-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0111c-119">Konstanta</span><span class="sxs-lookup"><span data-stu-id="0111c-119">Constant</span></span>  |<span data-ttu-id="0111c-120">Value</span><span class="sxs-lookup"><span data-stu-id="0111c-120">Value</span></span>  |<span data-ttu-id="0111c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0111c-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="0111c-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0111c-122">0x80041002</span></span> | <span data-ttu-id="0111c-123">Zadaná vlastnost nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="0111c-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0111c-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0111c-124">0x80041006</span></span> | <span data-ttu-id="0111c-125">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="0111c-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0111c-126">0</span><span class="sxs-lookup"><span data-stu-id="0111c-126">0</span></span> | <span data-ttu-id="0111c-127">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0111c-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0111c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0111c-128">Remarks</span></span>

<span data-ttu-id="0111c-129">Tato funkce zalomí volání metody [IWbemclassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="0111c-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="0111c-130">Správa systému Windows může nastavit ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) na `null` hodnotu, pokud metoda nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="0111c-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="0111c-131">V `ppInSignature` systémech `ppOutSignature` a popište parametry a výstupní parametry v uvedeném pořadí jako vlastnosti `IWbemClassObject` instance třídy System Class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="0111c-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="0111c-132">`ppInSignature` Vlastnosti v `Param`mají název *n*, kde *n* je pozice parametru v signatuře metody (například `Param1`, `Param2`atd.).</span><span class="sxs-lookup"><span data-stu-id="0111c-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="0111c-133">Vlastnosti v `ppOutSignature` jsou také pojmenované `Param` *n*a návratová hodnota je pojmenována `ReturnValue`.</span><span class="sxs-lookup"><span data-stu-id="0111c-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="0111c-134">Další informace a příklad naleznete v tématu [Metoda IWbemclassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="0111c-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="0111c-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0111c-135">Requirements</span></span>

<span data-ttu-id="0111c-136">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0111c-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0111c-137">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0111c-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="0111c-138">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0111c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0111c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0111c-139">See also</span></span>

- [<span data-ttu-id="0111c-140">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="0111c-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
