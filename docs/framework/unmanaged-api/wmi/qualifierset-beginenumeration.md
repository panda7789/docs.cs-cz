---
title: Funkce QualifierSet_BeginEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_BeginEnumeration resetuje enumerátor kvalifikátory objektu.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3577c90af51886868d57796fb5bfae91dedcee16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720116"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="e2926-103">QualifierSet_BeginEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="e2926-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="e2926-104">Návrat na začátek výčtu enumerátor kvalifikátory objektu.</span><span class="sxs-lookup"><span data-stu-id="e2926-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e2926-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2926-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="e2926-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2926-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="e2926-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e2926-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e2926-108">[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="e2926-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="e2926-109">[in] Bitová kombinace příznaků nebo podle hodnoty [poznámky](#remarks) oddíl, který určuje kvalifikátory zahrnout do výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2926-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e2926-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2926-110">Return value</span></span>

<span data-ttu-id="e2926-111">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e2926-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e2926-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e2926-112">Constant</span></span>  |<span data-ttu-id="e2926-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e2926-113">Value</span></span>  |<span data-ttu-id="e2926-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e2926-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e2926-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e2926-115">0x80041008</span></span> | <span data-ttu-id="e2926-116">`lFlags` Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e2926-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="e2926-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="e2926-117">0x8004101d</span></span> | <span data-ttu-id="e2926-118">Druhé volání `QualifierSet_BeginEnumeration` proběhla bez opětovné volání [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e2926-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e2926-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e2926-119">0x80041006</span></span> | <span data-ttu-id="e2926-120">Nedostatek paměti je k dispozici zahájíte nový výčet.</span><span class="sxs-lookup"><span data-stu-id="e2926-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e2926-121">0</span><span class="sxs-lookup"><span data-stu-id="e2926-121">0</span></span> | <span data-ttu-id="e2926-122">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e2926-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e2926-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2926-123">Remarks</span></span>

<span data-ttu-id="e2926-124">Tato funkce zalamuje volání na [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="e2926-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="e2926-125">K vytvoření výčtu všech kvalifikátory pro objekt, musí tuto metodu volat před prvním volání [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="e2926-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="e2926-126">Pořadí, ve kterém jsou uvedené kvalifikátory je zaručeno, že bude neutrální pro daný výčet.</span><span class="sxs-lookup"><span data-stu-id="e2926-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="e2926-127">Příznaky, které mohou být předány jako `lEnumFlags` argument jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e2926-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="e2926-128">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e2926-128">Constant</span></span>  |<span data-ttu-id="e2926-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e2926-129">Value</span></span>  |<span data-ttu-id="e2926-130">Popis</span><span class="sxs-lookup"><span data-stu-id="e2926-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="e2926-131">0</span><span class="sxs-lookup"><span data-stu-id="e2926-131">0</span></span> | <span data-ttu-id="e2926-132">Vrátí názvy všech kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="e2926-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="e2926-133">0x10</span><span class="sxs-lookup"><span data-stu-id="e2926-133">0x10</span></span> | <span data-ttu-id="e2926-134">Vrátíte pouze názvy kvalifikátory konkrétní aktuální vlastnost nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="e2926-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="e2926-135">Pro vlastnost: Vrátí jenom v kvalifikátorech specifické pro vlastnost (včetně potlačení) a ne kvalifikátory, rozšířena z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="e2926-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="e2926-136">Pro instanci: Vrátíte pouze názvy instancí kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e2926-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="e2926-137">Pro třídu: Vrátíte pouze kvalifikátory konkrétní beiong třída odvozena.</span><span class="sxs-lookup"><span data-stu-id="e2926-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="e2926-138">0x20</span><span class="sxs-lookup"><span data-stu-id="e2926-138">0x20</span></span> | <span data-ttu-id="e2926-139">Vrátit pouze názvy kvalifikátory rozšířena z jiného objektu.</span><span class="sxs-lookup"><span data-stu-id="e2926-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="e2926-140">Pro vlastnost: Vrátit se rozšířit jenom v kvalifikátorech k této vlastnosti z definice třídy a ne ty ze samotné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e2926-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="e2926-141">Pro instanci: Vrátit pouze ty kvalifikátory rozšířena z definice třídy.</span><span class="sxs-lookup"><span data-stu-id="e2926-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="e2926-142">Pro třídu: Vrátit pouze názvy kvalifikátor zděděná z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="e2926-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e2926-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2926-143">Requirements</span></span>  
 <span data-ttu-id="e2926-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2926-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2926-145">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e2926-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e2926-146">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e2926-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2926-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2926-147">See also</span></span>
- [<span data-ttu-id="e2926-148">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e2926-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
