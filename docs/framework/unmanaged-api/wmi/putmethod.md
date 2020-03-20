---
title: Funkce PutMethod (Unmanaged API Reference)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174911"
---
# <a name="putmethod-function"></a><span data-ttu-id="e3987-103">PutMethod</span><span class="sxs-lookup"><span data-stu-id="e3987-103">PutMethod function</span></span>
<span data-ttu-id="e3987-104">Vytvoří metodu.</span><span class="sxs-lookup"><span data-stu-id="e3987-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e3987-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3987-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="e3987-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3987-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e3987-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="e3987-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e3987-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="e3987-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="e3987-109">[v] Název metody, která má být vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e3987-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="e3987-110">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="e3987-110">[in] Reserved.</span></span> <span data-ttu-id="e3987-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="e3987-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="e3987-112">[v] Ukazatel na kopii [__Parameters systémové třídy,](/windows/desktop/WmiSdk/--parameters) která obsahuje `in` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="e3987-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="e3987-113">Tento parametr je ignorován, `null`pokud je nastavenna .</span><span class="sxs-lookup"><span data-stu-id="e3987-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="e3987-114">[v]  Ukazatel na kopii [__Parameters systémové třídy,](/windows/desktop/WmiSdk/--parameters) která obsahuje `out` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="e3987-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="e3987-115">Tento parametr je ignorován, `null`pokud je nastavenna .</span><span class="sxs-lookup"><span data-stu-id="e3987-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e3987-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e3987-116">Return value</span></span>

<span data-ttu-id="e3987-117">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e3987-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e3987-118">Trvalé</span><span class="sxs-lookup"><span data-stu-id="e3987-118">Constant</span></span>  |<span data-ttu-id="e3987-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e3987-119">Value</span></span>  |<span data-ttu-id="e3987-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e3987-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e3987-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e3987-121">0x80041008</span></span> | <span data-ttu-id="e3987-122">Jeden nebo více parametrů není platný.</span><span class="sxs-lookup"><span data-stu-id="e3987-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="e3987-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="e3987-123">0x80041043</span></span> | <span data-ttu-id="e3987-124">Parametr `[in, out]` metody zadaný v *objektech pInSignature* i *pOutSignature* má různé kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="e3987-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="e3987-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="e3987-125">0x80041036</span></span> | <span data-ttu-id="e3987-126">Parametr metody chybí specifikace kvalifikátoru **ID.**</span><span class="sxs-lookup"><span data-stu-id="e3987-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="e3987-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="e3987-127">0x80041038</span></span> | <span data-ttu-id="e3987-128">Řada ID, která je přiřazena parametrům metody, není po sobě jdoucí nebo nezačíná na hodnotě 0.</span><span class="sxs-lookup"><span data-stu-id="e3987-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="e3987-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="e3987-129">0x80041039</span></span> | <span data-ttu-id="e3987-130">Vrácená hodnota metody má kvalifikátor **ID.**</span><span class="sxs-lookup"><span data-stu-id="e3987-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="e3987-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="e3987-131">0x80041034</span></span> | <span data-ttu-id="e3987-132">Došlo k pokusu o opětovné použití existujícího názvu metody z nadřazené třídy a podpisy se neshodují.</span><span class="sxs-lookup"><span data-stu-id="e3987-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e3987-133">0</span><span class="sxs-lookup"><span data-stu-id="e3987-133">0</span></span> | <span data-ttu-id="e3987-134">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e3987-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e3987-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3987-135">Remarks</span></span>

<span data-ttu-id="e3987-136">Tato funkce zabalí volání metody [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="e3987-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="e3987-137">Toto volání metody `ptr` je podporováno pouze v případě, že je definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="e3987-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="e3987-138">Manipulace s metodami není k dispozici z ukazatelů [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) které odkazují na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="e3987-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="e3987-139">Uživatelé nemohou vytvářet metody s názvy, které začínají nebo končí podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="e3987-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="e3987-140">To to je vyhrazeno pro systémové třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e3987-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="e3987-141">Pro metodu `in` a `out` parametry jsou popsány jako vlastnosti v [objektech IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="e3987-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="e3987-142">Parametr `[in/out]` lze definovat přidáním stejné vlastnosti do obou `pInSignature` `pOutSignature` objektů, na které se vztahuje parametry a.</span><span class="sxs-lookup"><span data-stu-id="e3987-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="e3987-143">V tomto případě vlastnosti sdílejí stejnou hodnotu kvalifikátoru **ID.**</span><span class="sxs-lookup"><span data-stu-id="e3987-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="e3987-144">Každá vlastnost v [__Parameters](/windows/desktop/WmiSdk/--parameters) objektu třídy jiné než `ReturnValue` musí mít **id** kvalifikátor, nula číselná hodnota, která identifikuje pořadí, ve kterém se zobrazí parametry.</span><span class="sxs-lookup"><span data-stu-id="e3987-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="e3987-145">Žádné dva parametry mohou mít stejnou hodnotu **ID** a nelze přeskočit žádnou hodnotu **ID.**</span><span class="sxs-lookup"><span data-stu-id="e3987-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="e3987-146">Pokud dojde k některé `PutMethod` z `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`těchto podmínek, funkce vrátí .</span><span class="sxs-lookup"><span data-stu-id="e3987-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="e3987-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3987-147">Example</span></span>

<span data-ttu-id="e3987-148">Příklad naleznete v metodě [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="e3987-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3987-149">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3987-149">Requirements</span></span>  
 <span data-ttu-id="e3987-150">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3987-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3987-151">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e3987-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e3987-152">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e3987-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3987-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3987-153">See also</span></span>

- [<span data-ttu-id="e3987-154">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e3987-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
