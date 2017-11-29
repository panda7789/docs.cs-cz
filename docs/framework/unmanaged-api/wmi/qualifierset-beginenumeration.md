---
title: "Funkce QualifierSet_BeginEnumeration (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce QualifierSet_BeginEnumeration obnoví enumerátor kvalifikátory objektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f66df772032b8e96b4956f3ed9a5818e961bd919
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="8dd2d-103">QualifierSet_BeginEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="8dd2d-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="8dd2d-104">Návrat na začátek výčtu enumerátor kvalifikátory objektu.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8dd2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dd2d-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="8dd2d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dd2d-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="8dd2d-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="8dd2d-108">[v] Ukazatel na [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="8dd2d-109">[v] Bitová kombinace příznaků nebo hodnoty, které jsou popsané v [poznámky](#remarks) oddíl, který určuje kvalifikátory zahrnout ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8dd2d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8dd2d-110">Return value</span></span>

<span data-ttu-id="8dd2d-111">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="8dd2d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8dd2d-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8dd2d-112">Constant</span></span>  |<span data-ttu-id="8dd2d-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8dd2d-113">Value</span></span>  |<span data-ttu-id="8dd2d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8dd2d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8dd2d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8dd2d-115">0x80041008</span></span> | <span data-ttu-id="8dd2d-116">`lFlags` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="8dd2d-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8dd2d-117">0x8004101d</span></span> | <span data-ttu-id="8dd2d-118">Druhé volání `QualifierSet_BeginEnumeration` byl proveden bez použité volání [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8dd2d-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8dd2d-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8dd2d-119">0x80041006</span></span> | <span data-ttu-id="8dd2d-120">Je k dispozici zahájíte nové – výčet není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8dd2d-121">0</span><span class="sxs-lookup"><span data-stu-id="8dd2d-121">0</span></span> | <span data-ttu-id="8dd2d-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8dd2d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dd2d-123">Remarks</span></span>

<span data-ttu-id="8dd2d-124">Tato funkce zabalí volání [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="8dd2d-125">Výčet všech kvalifikátory na objekt, tato metoda musí být volána před prvním volání [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="8dd2d-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="8dd2d-126">Pořadí, ve kterém jsou uvedené kvalifikátory záruku, že se jako výchozí pro daný výčet.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="8dd2d-127">Příznaky, které lze předat jako `lEnumFlags` argument jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="8dd2d-128">Konstanta</span><span class="sxs-lookup"><span data-stu-id="8dd2d-128">Constant</span></span>  |<span data-ttu-id="8dd2d-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8dd2d-129">Value</span></span>  |<span data-ttu-id="8dd2d-130">Popis</span><span class="sxs-lookup"><span data-stu-id="8dd2d-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="8dd2d-131">0</span><span class="sxs-lookup"><span data-stu-id="8dd2d-131">0</span></span> | <span data-ttu-id="8dd2d-132">Vrátí názvy všech kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="8dd2d-133">0x10</span><span class="sxs-lookup"><span data-stu-id="8dd2d-133">0x10</span></span> | <span data-ttu-id="8dd2d-134">Vraťte pouze názvy kvalifikátory specifické pro aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="8dd2d-135">Pro vlastnost: vracet jenom kvalifikátory specifické pro vlastnost (včetně potlačení), a ne těchto kvalifikátory rozšíří z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="8dd2d-136">Pro instanci: vrátit pouze názvy kvalifikátor specifické pro instanci.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="8dd2d-137">Pro třídu: vracet jenom kvalifikátory specifické pro beiong třídy odvozené.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="8dd2d-138">0x20</span><span class="sxs-lookup"><span data-stu-id="8dd2d-138">0x20</span></span> | <span data-ttu-id="8dd2d-139">Vraťte se rozšíří pouze názvy kvalifikátory z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="8dd2d-140">Pro vlastnost: vrátit se rozšíří pouze kvalifikátory k této vlastnosti z definice třídy a ne z samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="8dd2d-141">Pro instanci: vrátí jenom ty kvalifikátory rozšíří z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="8dd2d-142">Pro třídu: vrátit pouze názvy kvalifikátor zděděn od nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="8dd2d-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="8dd2d-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8dd2d-143">Requirements</span></span>  
 <span data-ttu-id="8dd2d-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dd2d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd2d-145">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8dd2d-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8dd2d-146">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8dd2d-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd2d-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dd2d-147">See also</span></span>  
[<span data-ttu-id="8dd2d-148">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="8dd2d-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
