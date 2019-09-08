---
title: Delete – funkce (odkaz na nespravované rozhraní API)
description: Funkce delete odstraní zadanou vlastnost a všechny její kvalifikátory z definice třídy CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798666"
---
# <a name="delete-function"></a><span data-ttu-id="f094b-103">Funkce Delete</span><span class="sxs-lookup"><span data-stu-id="f094b-103">Delete function</span></span>

<span data-ttu-id="f094b-104">Odstraní zadanou vlastnost a všechny její kvalifikátory z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="f094b-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f094b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f094b-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="f094b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f094b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="f094b-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f094b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="f094b-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="f094b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="f094b-109">pro Název vlastnosti, která se má odstranit</span><span class="sxs-lookup"><span data-stu-id="f094b-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="f094b-110">`wszName`musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="f094b-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f094b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f094b-111">Return value</span></span>

<span data-ttu-id="f094b-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f094b-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f094b-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f094b-113">Constant</span></span>  |<span data-ttu-id="f094b-114">Value</span><span class="sxs-lookup"><span data-stu-id="f094b-114">Value</span></span>  |<span data-ttu-id="f094b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f094b-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f094b-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f094b-116">0x80041001</span></span> | <span data-ttu-id="f094b-117">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="f094b-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="f094b-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="f094b-118">0x80041016</span></span> | <span data-ttu-id="f094b-119">Vlastnost nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="f094b-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f094b-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f094b-120">0x80041008</span></span> | <span data-ttu-id="f094b-121">Formát  `wszName` je neplatný.</span><span class="sxs-lookup"><span data-stu-id="f094b-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f094b-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f094b-122">0x80041002</span></span> | <span data-ttu-id="f094b-123">Zadaná vlastnost neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f094b-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f094b-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f094b-124">0x80041006</span></span> | <span data-ttu-id="f094b-125">K dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f094b-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="f094b-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="f094b-126">0x8004101c</span></span> | <span data-ttu-id="f094b-127">Vlastnost je zděděna ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="f094b-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="f094b-128">Vlastnost je systémová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f094b-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f094b-129">0</span><span class="sxs-lookup"><span data-stu-id="f094b-129">0</span></span> | <span data-ttu-id="f094b-130">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f094b-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="f094b-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="f094b-131">0x80041030</span></span> | <span data-ttu-id="f094b-132">Funkce odstranila výchozí hodnotu přepisu pro aktuální třídu.</span><span class="sxs-lookup"><span data-stu-id="f094b-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="f094b-133">Výchozí hodnota této vlastnosti v nadřazené třídě byla znovu aktivována.</span><span class="sxs-lookup"><span data-stu-id="f094b-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f094b-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f094b-134">Remarks</span></span>

<span data-ttu-id="f094b-135">Tato funkce zalomí volání metody [IWbemclassObject::D dstranit](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .</span><span class="sxs-lookup"><span data-stu-id="f094b-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f094b-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f094b-136">Requirements</span></span>

<span data-ttu-id="f094b-137">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f094b-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f094b-138">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f094b-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f094b-139">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f094b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f094b-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f094b-140">See also</span></span>

- [<span data-ttu-id="f094b-141">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f094b-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
