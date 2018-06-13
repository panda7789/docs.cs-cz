---
title: Funkce Next (referenční dokumentace nespravovaného rozhraní API)
description: Další funkce retireves další vlastnosti ve výčtu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e945930a9a668d0a1c1e4c26bf3add9cc574c261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461425"
---
# <a name="next-function"></a><span data-ttu-id="6a64e-103">Další funkce</span><span class="sxs-lookup"><span data-stu-id="6a64e-103">Next function</span></span>
<span data-ttu-id="6a64e-104">Načte další vlastnosti v výčet, který začíná volání [funkce BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6a64e-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6a64e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a64e-105">Syntax</span></span>  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a><span data-ttu-id="6a64e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a64e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6a64e-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="6a64e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6a64e-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="6a64e-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="6a64e-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="6a64e-109">[in] Reserved.</span></span> <span data-ttu-id="6a64e-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="6a64e-110">This parameter must be 0.</span></span>

`pstrName`  
<span data-ttu-id="6a64e-111">[out] Nový `BSTR` obsahující název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="6a64e-112">Tento parametr můžete nastavit `null` Pokud název není potřeba.</span><span class="sxs-lookup"><span data-stu-id="6a64e-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`  
<span data-ttu-id="6a64e-113">[out] A `VARIANT` vyplněnou hodnotou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="6a64e-114">Tento parametr můžete nastavit `null` Pokud hodnota není potřeba.</span><span class="sxs-lookup"><span data-stu-id="6a64e-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="6a64e-115">Pokud funkce vrátí kód chyby `VARIANT` předaný `pVal` je ponechat beze změny doleva.</span><span class="sxs-lookup"><span data-stu-id="6a64e-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span> 

`pvtType`  
<span data-ttu-id="6a64e-116">[out] Ukazatel na `CIMTYPE` proměnné ( `LONG` do které je umístěn typu vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="6a64e-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="6a64e-117">Hodnota této vlastnosti může být `VT_NULL_VARIANT`, v takovém případě je třeba určit skutečný typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="6a64e-118">Tento parametr může být také `null`.</span><span class="sxs-lookup"><span data-stu-id="6a64e-118">This parameter can also be `null`.</span></span> 

`plFlavor`  
<span data-ttu-id="6a64e-119">[out] `null`, nebo hodnotu, která přijímá informace o původu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="6a64e-120">Možné hodnoty v části [poznámky].</span><span class="sxs-lookup"><span data-stu-id="6a64e-120">See the [Remarks] section for possible values.</span></span> 

## <a name="return-value"></a><span data-ttu-id="6a64e-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a64e-121">Return value</span></span>

<span data-ttu-id="6a64e-122">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="6a64e-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6a64e-123">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6a64e-123">Constant</span></span>  |<span data-ttu-id="6a64e-124">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a64e-124">Value</span></span>  |<span data-ttu-id="6a64e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6a64e-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="6a64e-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6a64e-126">0x80041001</span></span> | <span data-ttu-id="6a64e-127">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="6a64e-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6a64e-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6a64e-128">0x80041008</span></span> | <span data-ttu-id="6a64e-129">Parametr je neplatný.</span><span class="sxs-lookup"><span data-stu-id="6a64e-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="6a64e-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6a64e-130">0x8004101d</span></span> | <span data-ttu-id="6a64e-131">Byl bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6a64e-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6a64e-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6a64e-132">0x80041006</span></span> | <span data-ttu-id="6a64e-133">Je k dispozici zahájíte nové – výčet není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6a64e-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6a64e-134">0x80041015</span></span> | <span data-ttu-id="6a64e-135">Vzdálené volání procedur od aktuálním procesem a správa systému Windows se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6a64e-135">The remote procedure call betweeen the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6a64e-136">0</span><span class="sxs-lookup"><span data-stu-id="6a64e-136">0</span></span> | <span data-ttu-id="6a64e-137">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6a64e-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="6a64e-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="6a64e-138">0x40005</span></span> | <span data-ttu-id="6a64e-139">Ve výčtu nejsou žádné další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a64e-139">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6a64e-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a64e-140">Remarks</span></span>

<span data-ttu-id="6a64e-141">Tato funkce zabalí volání [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="6a64e-141">This function wraps a call to the [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="6a64e-142">Tato metoda také vrátí hodnotu vlastnosti systému.</span><span class="sxs-lookup"><span data-stu-id="6a64e-142">This method also returns system properties.</span></span>

<span data-ttu-id="6a64e-143">Pokud základní typ vlastnosti je cesta k objektu, datum nebo čas nebo jiné speciální typ, pak typ vrácený neobsahuje dostatek informací.</span><span class="sxs-lookup"><span data-stu-id="6a64e-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="6a64e-144">Volající musí zkontrolovat `CIMTYPE` pro zadanou vlastnost k určení, zda je vlastnost odkaz na objekt, datum nebo čas nebo jiné speciální typu.</span><span class="sxs-lookup"><span data-stu-id="6a64e-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="6a64e-145">Pokud `plFlavor` není `null`, `LONG` hodnota obdrží informace o zdroji vlastnosti, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="6a64e-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="6a64e-146">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6a64e-146">Constant</span></span>  |<span data-ttu-id="6a64e-147">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6a64e-147">Value</span></span>  |<span data-ttu-id="6a64e-148">Popis</span><span class="sxs-lookup"><span data-stu-id="6a64e-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="6a64e-149">0x40</span><span class="sxs-lookup"><span data-stu-id="6a64e-149">0x40</span></span> | <span data-ttu-id="6a64e-150">Vlastnost je standardní systém vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a64e-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="6a64e-151">0x20</span><span class="sxs-lookup"><span data-stu-id="6a64e-151">0x20</span></span> | <span data-ttu-id="6a64e-152">Pro třídu: vlastnost je zděděna od nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="6a64e-152">For a class: The property is inherited from the parent class.</span></span> </br> <span data-ttu-id="6a64e-153">Pro instanci: vlastnost, zatímco zděděn od nadřazené třídy, se nezměnil instance.</span><span class="sxs-lookup"><span data-stu-id="6a64e-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="6a64e-154">0</span><span class="sxs-lookup"><span data-stu-id="6a64e-154">0</span></span> | <span data-ttu-id="6a64e-155">Pro třídu: vlastnost náleží do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="6a64e-155">For a class: The property belongs to the derived class.</span></span> </br> <span data-ttu-id="6a64e-156">Pro instanci: vlastnost je upravovat instance; To znamená, že byla zadána hodnota, nebo kvalifikátor byla přidána nebo upravena.</span><span class="sxs-lookup"><span data-stu-id="6a64e-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6a64e-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a64e-157">Requirements</span></span>  
 <span data-ttu-id="6a64e-158">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a64e-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a64e-159">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6a64e-159">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6a64e-160">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a64e-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a64e-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a64e-161">See also</span></span>  
[<span data-ttu-id="6a64e-162">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6a64e-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
