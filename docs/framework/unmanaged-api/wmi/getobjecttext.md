---
title: Funkce GetObjectText (referenční dokumentace nespravovaného rozhraní API)
description: Funkce GetObjectText vrací textové vykreslování objektu v syntaxi MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746493"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="de255-103">Funkce GetObjectText</span><span class="sxs-lookup"><span data-stu-id="de255-103">GetObjectText function</span></span>
<span data-ttu-id="de255-104">Vrátí textovou vykreslování objektu v syntaxi formátu MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="de255-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="de255-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de255-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="de255-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de255-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="de255-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="de255-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="de255-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="de255-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="de255-109">[in] Obvykle 0.</span><span class="sxs-lookup"><span data-stu-id="de255-109">[in] Normally 0.</span></span> <span data-ttu-id="de255-110">Pokud `WBEM_FLAG_NO_FLAVORS` (nebo 0x1) je zadán kvalifikátory jsou zahrnuty bez informací o šíření nebo flavor.</span><span class="sxs-lookup"><span data-stu-id="de255-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="de255-111">[out] Ukazatel `null` při vstupu.</span><span class="sxs-lookup"><span data-stu-id="de255-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="de255-112">Na vrátit, nově přidělenou `BSTR` , který obsahuje syntaxi MOF vykreslení objektu.</span><span class="sxs-lookup"><span data-stu-id="de255-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="de255-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="de255-113">Return value</span></span>

<span data-ttu-id="de255-114">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="de255-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="de255-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="de255-115">Constant</span></span>  |<span data-ttu-id="de255-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="de255-116">Value</span></span>  |<span data-ttu-id="de255-117">Popis</span><span class="sxs-lookup"><span data-stu-id="de255-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="de255-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="de255-118">0x80041001</span></span> | <span data-ttu-id="de255-119">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="de255-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="de255-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="de255-120">0x80041008</span></span> | <span data-ttu-id="de255-121">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="de255-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="de255-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="de255-122">0x80041006</span></span> | <span data-ttu-id="de255-123">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="de255-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="de255-124">0</span><span class="sxs-lookup"><span data-stu-id="de255-124">0</span></span> | <span data-ttu-id="de255-125">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="de255-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="de255-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de255-126">Remarks</span></span>

<span data-ttu-id="de255-127">Tato funkce zalamuje volání na [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) metody.</span><span class="sxs-lookup"><span data-stu-id="de255-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="de255-128">MOF text vracený při neobsahuje všechny informace o objektu, ale pouze dostatek informací pro kompilátoru MOF být schopni obnovit na původní objekt.</span><span class="sxs-lookup"><span data-stu-id="de255-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="de255-129">Žádné rozšíří kvalifikátory nebo vlastnosti nadřazené třídu pro instanci, jsou zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="de255-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="de255-130">Následující požadovaný algoritmus se používá k rekonstrukci text parametry metody:</span><span class="sxs-lookup"><span data-stu-id="de255-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="de255-131">Parametry jsou resequenced v pořadí hodnot jejich identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="de255-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="de255-132">Parametry, které jsou určeny jako `[in]` a `[out]` jsou sloučeny do jediného parametru.</span><span class="sxs-lookup"><span data-stu-id="de255-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="de255-133">`pstrObjectText` musí být ukazatel `null` při volání funkce; nesmí odkazovat na řetězec, který je platný před voláním metody, protože ukazatel nebudou uvolněný.</span><span class="sxs-lookup"><span data-stu-id="de255-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="de255-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de255-134">Requirements</span></span>  
<span data-ttu-id="de255-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de255-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de255-136">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="de255-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="de255-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="de255-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de255-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de255-138">See also</span></span>

- [<span data-ttu-id="de255-139">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="de255-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
