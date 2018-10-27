---
title: Funkce PutMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutMethod vytvoří metodu.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98ef688c1136a81a5b57c3fdfee73c53024186e7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191035"
---
# <a name="putmethod-function"></a><span data-ttu-id="dde9e-103">PutMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="dde9e-103">PutMethod function</span></span>
<span data-ttu-id="dde9e-104">Vytvoří metodu.</span><span class="sxs-lookup"><span data-stu-id="dde9e-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="dde9e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dde9e-105">Syntax</span></span>  
  
```  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="dde9e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dde9e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="dde9e-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="dde9e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="dde9e-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="dde9e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="dde9e-109">[in] Název metody k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="dde9e-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="dde9e-110">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="dde9e-110">[in] Reserved.</span></span> <span data-ttu-id="dde9e-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="dde9e-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="dde9e-112">[in] Ukazatel na kopii [třída systému __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `in` parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="dde9e-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="dde9e-113">Tento parametr se ignoruje, pokud nastavit `null`.</span><span class="sxs-lookup"><span data-stu-id="dde9e-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="dde9e-114">[in]  Ukazatel na kopii [třída systému __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje `out` parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="dde9e-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="dde9e-115">Tento parametr se ignoruje, pokud nastavit `null`.</span><span class="sxs-lookup"><span data-stu-id="dde9e-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="dde9e-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dde9e-116">Return value</span></span>

<span data-ttu-id="dde9e-117">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="dde9e-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="dde9e-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="dde9e-118">Constant</span></span>  |<span data-ttu-id="dde9e-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dde9e-119">Value</span></span>  |<span data-ttu-id="dde9e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="dde9e-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="dde9e-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="dde9e-121">0x80041008</span></span> | <span data-ttu-id="dde9e-122">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="dde9e-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="dde9e-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="dde9e-123">0x80041043</span></span> | <span data-ttu-id="dde9e-124">`[in, out]` Parametr metody určené v i *pInSignature* a *pOutSignature* objekty mají různé kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="dde9e-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="dde9e-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="dde9e-125">0x80041036</span></span> | <span data-ttu-id="dde9e-126">Parametr metody chybí specifikace **ID** kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="dde9e-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="dde9e-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="dde9e-127">0x80041038</span></span> | <span data-ttu-id="dde9e-128">ID série, která je přiřazena k parametrům metody není po sobě jdoucích nebo není začínají hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="dde9e-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="dde9e-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="dde9e-129">0x80041039</span></span> | <span data-ttu-id="dde9e-130">Návratová hodnota metody má **ID** kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="dde9e-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="dde9e-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="dde9e-131">0x80041034</span></span> | <span data-ttu-id="dde9e-132">Byl proveden pokus o opakované použití existující název metody od nadřazené třídy a podpisy se neshodují.</span><span class="sxs-lookup"><span data-stu-id="dde9e-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="dde9e-133">0</span><span class="sxs-lookup"><span data-stu-id="dde9e-133">0</span></span> | <span data-ttu-id="dde9e-134">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="dde9e-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="dde9e-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dde9e-135">Remarks</span></span>

<span data-ttu-id="dde9e-136">Tato funkce zalamuje volání na [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="dde9e-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="dde9e-137">Volání této metody je podporována pouze v případě `ptr` je definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="dde9e-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="dde9e-138">Zpracování metody není k dispozici [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ukazatele, které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="dde9e-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="dde9e-139">Uživatelé nemůžou vytvářet metody s názvy, které začínat ani končit podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="dde9e-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="dde9e-140">To je vyhrazen pro systémové třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dde9e-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="dde9e-141">Pro metodu `in` a `out` jsou popsány parametry jako vlastnosti v [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objekty.</span><span class="sxs-lookup"><span data-stu-id="dde9e-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="dde9e-142">`[in/out]` Parametr může být definován tak, že přidáte na oba objekty, na které odkazují stejnou vlastnost `pInSignature` a `pOutSignature` parametry.</span><span class="sxs-lookup"><span data-stu-id="dde9e-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="dde9e-143">V takovém případě vlastnosti sdílet stejný **ID** hodnotu kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="dde9e-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="dde9e-144">Každou vlastnost v [__Parameters](/windows/desktop/WmiSdk/--parameters) třídy objektů jiných než `ReturnValue` musí mít **ID** kvalifikátor, založený na nule, který identifikuje pořadí parametrů číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dde9e-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="dde9e-145">Žádné dva parametry můžou mít stejný **ID** hodnotu a ne **ID** hodnoty mohou být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="dde9e-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="dde9e-146">Pokud dojde k některou z podmínek, `PutMethod` vrací funkce `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="dde9e-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="dde9e-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="dde9e-147">Example</span></span>

<span data-ttu-id="dde9e-148">Příklad najdete v tématu [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="dde9e-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dde9e-149">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dde9e-149">Requirements</span></span>  
 <span data-ttu-id="dde9e-150">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde9e-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde9e-151">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="dde9e-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="dde9e-152">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dde9e-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde9e-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dde9e-153">See also</span></span>  
[<span data-ttu-id="dde9e-154">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="dde9e-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
