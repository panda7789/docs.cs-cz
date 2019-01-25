---
title: Funkce QualifierSet_Put (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_Put zapisuje s názvem kvalifikátoru a její hodnotu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1fc8d9d8c135f9eea8b9451b884ef3b7ba4704
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694136"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="ff28d-103">QualifierSet_Put – funkce</span><span class="sxs-lookup"><span data-stu-id="ff28d-103">QualifierSet_Put function</span></span>
<span data-ttu-id="ff28d-104">Zapíše s názvem kvalifikátoru a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ff28d-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="ff28d-105">Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="ff28d-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="ff28d-106">Pokud kvalifikátor buď neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="ff28d-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ff28d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff28d-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="ff28d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff28d-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="ff28d-109">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ff28d-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ff28d-110">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="ff28d-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="ff28d-111">[in] Název kvalifikátor pro zápis.</span><span class="sxs-lookup"><span data-stu-id="ff28d-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="ff28d-112">`pVal` [in] Ukazatel na platný `VARIANT` , který obsahuje kvalifikátor pro zápis.</span><span class="sxs-lookup"><span data-stu-id="ff28d-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="ff28d-113">Tento parametr nemůže mít `null`.</span><span class="sxs-lookup"><span data-stu-id="ff28d-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="ff28d-114">`lFlavor` [in] Jeden z následujících konstant, které definuje požadovaný flavor u tohoto kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ff28d-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="ff28d-115">Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="ff28d-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="ff28d-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ff28d-116">Constant</span></span>  |<span data-ttu-id="ff28d-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff28d-117">Value</span></span>  |<span data-ttu-id="ff28d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ff28d-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="ff28d-119">0</span><span class="sxs-lookup"><span data-stu-id="ff28d-119">0</span></span> | <span data-ttu-id="ff28d-120">Kvalifikátor se dá přepsat v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="ff28d-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="ff28d-121">**Toto je výchozí hodnota.**</span><span class="sxs-lookup"><span data-stu-id="ff28d-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="ff28d-122">1</span><span class="sxs-lookup"><span data-stu-id="ff28d-122">1</span></span> | <span data-ttu-id="ff28d-123">Kvalifikátor je postoupena do instance.</span><span class="sxs-lookup"><span data-stu-id="ff28d-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="ff28d-124">2</span><span class="sxs-lookup"><span data-stu-id="ff28d-124">2</span></span> | <span data-ttu-id="ff28d-125">Kvalifikátor je postoupena do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ff28d-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="ff28d-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="ff28d-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="ff28d-127">0x10</span><span class="sxs-lookup"><span data-stu-id="ff28d-127">0x10</span></span> | <span data-ttu-id="ff28d-128">Kvalifikátor nelze přepsat v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="ff28d-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="ff28d-129">\`WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="ff28d-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="ff28d-130">0x80</span><span class="sxs-lookup"><span data-stu-id="ff28d-130">0x80</span></span> | <span data-ttu-id="ff28d-131">Kvalifikátor je lokalizován.</span><span class="sxs-lookup"><span data-stu-id="ff28d-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="ff28d-132">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff28d-132">Return value</span></span>

<span data-ttu-id="ff28d-133">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ff28d-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ff28d-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ff28d-134">Constant</span></span>  |<span data-ttu-id="ff28d-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff28d-135">Value</span></span>  |<span data-ttu-id="ff28d-136">Popis</span><span class="sxs-lookup"><span data-stu-id="ff28d-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="ff28d-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="ff28d-137">0x8004101f</span></span> | <span data-ttu-id="ff28d-138">Došlo k neplatnému pokusu určit **klíč** kvalifikátor na vlastnost, která nemůže být klíč.</span><span class="sxs-lookup"><span data-stu-id="ff28d-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="ff28d-139">Klíče jsou zadány om c; detaily třídy definice objektu a nelze je měnit na základě jednotlivé instance.</span><span class="sxs-lookup"><span data-stu-id="ff28d-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ff28d-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ff28d-140">0x80041008</span></span> | <span data-ttu-id="ff28d-141">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="ff28d-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="ff28d-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="ff28d-142">0x80041029</span></span> | <span data-ttu-id="ff28d-143">`pVal` Parametr není platný typ kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ff28d-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="ff28d-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="ff28d-144">0x8004101a</span></span> | <span data-ttu-id="ff28d-145">Není možné volat `QualifierSet_Put` metoda na kvalifikátor, protože vlastnící objekt nepovoluje přepíše.</span><span class="sxs-lookup"><span data-stu-id="ff28d-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ff28d-146">0</span><span class="sxs-lookup"><span data-stu-id="ff28d-146">0</span></span> | <span data-ttu-id="ff28d-147">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ff28d-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ff28d-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff28d-148">Remarks</span></span>

<span data-ttu-id="ff28d-149">Tato funkce zalamuje volání na [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) metody.</span><span class="sxs-lookup"><span data-stu-id="ff28d-149">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff28d-150">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff28d-150">Requirements</span></span>  
 <span data-ttu-id="ff28d-151">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff28d-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff28d-152">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ff28d-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ff28d-153">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff28d-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff28d-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff28d-154">See also</span></span>
- [<span data-ttu-id="ff28d-155">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ff28d-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
