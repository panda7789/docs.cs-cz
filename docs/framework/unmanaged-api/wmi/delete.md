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
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127667"
---
# <a name="delete-function"></a><span data-ttu-id="eea80-103">Funkce Delete</span><span class="sxs-lookup"><span data-stu-id="eea80-103">Delete function</span></span>

<span data-ttu-id="eea80-104">Odstraní zadanou vlastnost a všechny její kvalifikátory z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="eea80-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="eea80-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eea80-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="eea80-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eea80-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="eea80-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="eea80-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="eea80-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="eea80-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="eea80-109">pro Název vlastnosti, která se má odstranit</span><span class="sxs-lookup"><span data-stu-id="eea80-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="eea80-110">`wszName` musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="eea80-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="eea80-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eea80-111">Return value</span></span>

<span data-ttu-id="eea80-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="eea80-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eea80-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="eea80-113">Constant</span></span>  |<span data-ttu-id="eea80-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="eea80-114">Value</span></span>  |<span data-ttu-id="eea80-115">Popis</span><span class="sxs-lookup"><span data-stu-id="eea80-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="eea80-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="eea80-116">0x80041001</span></span> | <span data-ttu-id="eea80-117">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="eea80-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="eea80-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="eea80-118">0x80041016</span></span> | <span data-ttu-id="eea80-119">Vlastnost nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="eea80-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eea80-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eea80-120">0x80041008</span></span> | <span data-ttu-id="eea80-121">Formát  `wszName` je neplatný.</span><span class="sxs-lookup"><span data-stu-id="eea80-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="eea80-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eea80-122">0x80041002</span></span> | <span data-ttu-id="eea80-123">Zadaná vlastnost neexistuje.</span><span class="sxs-lookup"><span data-stu-id="eea80-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="eea80-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="eea80-124">0x80041006</span></span> | <span data-ttu-id="eea80-125">K dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="eea80-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="eea80-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="eea80-126">0x8004101c</span></span> | <span data-ttu-id="eea80-127">Vlastnost je zděděna ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="eea80-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="eea80-128">Vlastnost je systémová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eea80-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eea80-129">0,8</span><span class="sxs-lookup"><span data-stu-id="eea80-129">0</span></span> | <span data-ttu-id="eea80-130">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="eea80-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="eea80-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="eea80-131">0x80041030</span></span> | <span data-ttu-id="eea80-132">Funkce odstranila výchozí hodnotu přepisu pro aktuální třídu.</span><span class="sxs-lookup"><span data-stu-id="eea80-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="eea80-133">Výchozí hodnota této vlastnosti v nadřazené třídě byla znovu aktivována.</span><span class="sxs-lookup"><span data-stu-id="eea80-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="eea80-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eea80-134">Remarks</span></span>

<span data-ttu-id="eea80-135">Tato funkce zalomí volání metody [IWbemclassObject::D dstranit](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .</span><span class="sxs-lookup"><span data-stu-id="eea80-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eea80-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eea80-136">Requirements</span></span>

<span data-ttu-id="eea80-137">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eea80-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="eea80-138">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="eea80-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="eea80-139">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eea80-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="eea80-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eea80-140">See also</span></span>

- [<span data-ttu-id="eea80-141">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="eea80-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
