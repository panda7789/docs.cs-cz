---
title: Odstranit funkci (referenční dokumentace nespravovaného rozhraní API)
description: Funkce Delete Odstraní zadané vlastnosti a všechny jeho kvalifikátory z definice třídy CIM.
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
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578915"
---
# <a name="delete-function"></a><span data-ttu-id="bdb95-103">Odstranit funkci</span><span class="sxs-lookup"><span data-stu-id="bdb95-103">Delete function</span></span>
<span data-ttu-id="bdb95-104">Odstraní zadanou vlastnost a všechny jeho kvalifikátory z definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="bdb95-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bdb95-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb95-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="bdb95-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdb95-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bdb95-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="bdb95-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bdb95-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="bdb95-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="bdb95-109">[in] Název vlastnosti, která má odstranit.</span><span class="sxs-lookup"><span data-stu-id="bdb95-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="bdb95-110">`wszName` musí být ukazatel na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="bdb95-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="bdb95-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bdb95-111">Return value</span></span>

<span data-ttu-id="bdb95-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="bdb95-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bdb95-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bdb95-113">Constant</span></span>  |<span data-ttu-id="bdb95-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bdb95-114">Value</span></span>  |<span data-ttu-id="bdb95-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bdb95-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bdb95-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bdb95-116">0x80041001</span></span> | <span data-ttu-id="bdb95-117">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="bdb95-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="bdb95-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="bdb95-118">0x80041016</span></span> | <span data-ttu-id="bdb95-119">Vlastnost nelze odstranit.</span><span class="sxs-lookup"><span data-stu-id="bdb95-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bdb95-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bdb95-120">0x80041008</span></span> | <span data-ttu-id="bdb95-121">Formát  `wszzName` je neplatný.</span><span class="sxs-lookup"><span data-stu-id="bdb95-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="bdb95-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="bdb95-122">0x80041002</span></span> | <span data-ttu-id="bdb95-123">Zadaná vlastnost neexistuje.</span><span class="sxs-lookup"><span data-stu-id="bdb95-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bdb95-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bdb95-124">0x80041006</span></span> | <span data-ttu-id="bdb95-125">Není k dispozici dostatek paměti k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="bdb95-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="bdb95-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="bdb95-126">0x8004101c</span></span> | <span data-ttu-id="bdb95-127">Vlastnost se dědí ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bdb95-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="bdb95-128">Vlastnost je vlastnost systému.</span><span class="sxs-lookup"><span data-stu-id="bdb95-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bdb95-129">0</span><span class="sxs-lookup"><span data-stu-id="bdb95-129">0</span></span> | <span data-ttu-id="bdb95-130">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bdb95-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="bdb95-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="bdb95-131">0x80041030</span></span> | <span data-ttu-id="bdb95-132">Funkce odstranit výchozí hodnotu pro aktuální třídu.</span><span class="sxs-lookup"><span data-stu-id="bdb95-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="bdb95-133">Výchozí hodnota této vlastnosti v nadřazené třídě byl reactiviated.</span><span class="sxs-lookup"><span data-stu-id="bdb95-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="bdb95-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdb95-134">Remarks</span></span>

<span data-ttu-id="bdb95-135">Tato funkce zalamuje volání na [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) metody.</span><span class="sxs-lookup"><span data-stu-id="bdb95-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdb95-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdb95-136">Requirements</span></span>  
 <span data-ttu-id="bdb95-137">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb95-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb95-138">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bdb95-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bdb95-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb95-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb95-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdb95-140">See also</span></span>  
[<span data-ttu-id="bdb95-141">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bdb95-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
