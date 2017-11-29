---
title: "Funkce QualifierSet_Put (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_Put zapíše pojmenované kvalifikátor a její hodnotu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Put
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Put
helpviewer_keywords: QualifierSet_Put function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7fdb6759d4e39ad9ab6bd6da2c2a0e2abfbe5d56
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="b927b-103">QualifierSet_Put – funkce</span><span class="sxs-lookup"><span data-stu-id="b927b-103">QualifierSet_Put function</span></span>
<span data-ttu-id="b927b-104">Zapíše kvalifikátor s názvem a hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b927b-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="b927b-105">Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="b927b-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="b927b-106">Pokud kvalifikátor neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="b927b-106">If the qualifier does not exist, it is created.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b927b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b927b-107">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a><span data-ttu-id="b927b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="b927b-108">Parameters</span></span>

`vFunc`   
<span data-ttu-id="b927b-109">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b927b-109">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="b927b-110">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="b927b-110">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="b927b-111">[v] Název kvalifikátor k zápisu.</span><span class="sxs-lookup"><span data-stu-id="b927b-111">[in] The name of the qualifier to write.</span></span>

<span data-ttu-id="b927b-112">`pVal`[v] Ukazatel na platnou `VARIANT` obsahující kvalifikátor k zápisu.</span><span class="sxs-lookup"><span data-stu-id="b927b-112">`pVal` [in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="b927b-113">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="b927b-113">This parameter cannot be `null`.</span></span>

<span data-ttu-id="b927b-114">`lFlavor`[v] Jeden z následujících konstanty, které definuje typů kvalifikátor požadované pro tento kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="b927b-114">`lFlavor` [in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="b927b-115">Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="b927b-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="b927b-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b927b-116">Constant</span></span>  |<span data-ttu-id="b927b-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b927b-117">Value</span></span>  |<span data-ttu-id="b927b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b927b-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="b927b-119">0</span><span class="sxs-lookup"><span data-stu-id="b927b-119">0</span></span> | <span data-ttu-id="b927b-120">Kvalifikátor můžete přepsání v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="b927b-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="b927b-121">**Toto je výchozí hodnota.**</span><span class="sxs-lookup"><span data-stu-id="b927b-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="b927b-122">1</span><span class="sxs-lookup"><span data-stu-id="b927b-122">1</span></span> | <span data-ttu-id="b927b-123">Kvalifikátor je rozšířena do instance.</span><span class="sxs-lookup"><span data-stu-id="b927b-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="b927b-124">2</span><span class="sxs-lookup"><span data-stu-id="b927b-124">2</span></span> | <span data-ttu-id="b927b-125">Kvalifikátor je rozšířena do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b927b-125">The qualifier is propagated to derived classes.</span></span> |
| <span data-ttu-id="b927b-126">' WBEM_FLAVOR_NOT_OVERRIDABLE</span><span class="sxs-lookup"><span data-stu-id="b927b-126">\`WBEM_FLAVOR_NOT_OVERRIDABLE</span></span> | <span data-ttu-id="b927b-127">0x10</span><span class="sxs-lookup"><span data-stu-id="b927b-127">0x10</span></span> | <span data-ttu-id="b927b-128">Kvalifikátor nelze přepsání v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="b927b-128">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| <span data-ttu-id="b927b-129">' WBEM_FLAVOR_AMENDED</span><span class="sxs-lookup"><span data-stu-id="b927b-129">\`WBEM_FLAVOR_AMENDED</span></span> | <span data-ttu-id="b927b-130">0x80</span><span class="sxs-lookup"><span data-stu-id="b927b-130">0x80</span></span> | <span data-ttu-id="b927b-131">Kvalifikátor je lokalizované.</span><span class="sxs-lookup"><span data-stu-id="b927b-131">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="b927b-132">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b927b-132">Return value</span></span>

<span data-ttu-id="b927b-133">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="b927b-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b927b-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b927b-134">Constant</span></span>  |<span data-ttu-id="b927b-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b927b-135">Value</span></span>  |<span data-ttu-id="b927b-136">Popis</span><span class="sxs-lookup"><span data-stu-id="b927b-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="b927b-137">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="b927b-137">0x8004101f</span></span> | <span data-ttu-id="b927b-138">Došlo k neplatnému pokusu zadejte **klíč** kvalifikátor u vlastnosti, která nemůže být klíčem.</span><span class="sxs-lookup"><span data-stu-id="b927b-138">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="b927b-139">Klíče jsou zadány om c; ass definici objektu a nelze je měnit u jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="b927b-139">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b927b-140">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b927b-140">0x80041008</span></span> | <span data-ttu-id="b927b-141">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="b927b-141">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="b927b-142">0x80041029</span><span class="sxs-lookup"><span data-stu-id="b927b-142">0x80041029</span></span> | <span data-ttu-id="b927b-143">`pVal` Parametr není platný typ kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b927b-143">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="b927b-144">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="b927b-144">0x8004101a</span></span> | <span data-ttu-id="b927b-145">Není možné volat `QualifierSet_Put` metodu kvalifikátor protože vlastnící objekt nepovoluje přepsání.</span><span class="sxs-lookup"><span data-stu-id="b927b-145">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b927b-146">0</span><span class="sxs-lookup"><span data-stu-id="b927b-146">0</span></span> | <span data-ttu-id="b927b-147">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b927b-147">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b927b-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b927b-148">Remarks</span></span>

<span data-ttu-id="b927b-149">Tato funkce zabalí volání [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="b927b-149">This function wraps a call to the [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b927b-150">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b927b-150">Requirements</span></span>  
 <span data-ttu-id="b927b-151">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b927b-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b927b-152">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b927b-152">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b927b-153">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b927b-153">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b927b-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="b927b-154">See also</span></span>  
[<span data-ttu-id="b927b-155">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b927b-155">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
