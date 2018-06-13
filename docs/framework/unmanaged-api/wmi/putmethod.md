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
ms.openlocfilehash: 7f74b0d30a1a8899d3c8d0a2bf0f108ea11165cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461850"
---
# <a name="putmethod-function"></a><span data-ttu-id="a6546-103">PutMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="a6546-103">PutMethod function</span></span>
<span data-ttu-id="a6546-104">Vytvoří metodu.</span><span class="sxs-lookup"><span data-stu-id="a6546-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a6546-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6546-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="a6546-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6546-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a6546-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a6546-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a6546-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="a6546-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="a6546-109">[v] Název metody pro vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a6546-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="a6546-110">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="a6546-110">[in] Reserved.</span></span> <span data-ttu-id="a6546-111">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="a6546-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="a6546-112">[v] Ukazatel na kopii [__Parameters systémové třídy](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) obsahující `in` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a6546-112">[in] A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="a6546-113">Tento parametr je ignorována, pokud nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="a6546-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="a6546-114">[v]  Ukazatel na kopii [__Parameters systémové třídy](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) obsahující `out` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a6546-114">[in]  A pointer to a copy of the [__Parameters system class](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="a6546-115">Tento parametr je ignorována, pokud nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="a6546-115">This parameter is ignored if set to `null`.</span></span>
 

## <a name="return-value"></a><span data-ttu-id="a6546-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a6546-116">Return value</span></span>

<span data-ttu-id="a6546-117">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="a6546-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a6546-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a6546-118">Constant</span></span>  |<span data-ttu-id="a6546-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a6546-119">Value</span></span>  |<span data-ttu-id="a6546-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a6546-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a6546-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a6546-121">0x80041008</span></span> | <span data-ttu-id="a6546-122">Jeden nebo více parametrů nejsou platné.</span><span class="sxs-lookup"><span data-stu-id="a6546-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="a6546-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="a6546-123">0x80041043</span></span> | <span data-ttu-id="a6546-124">`[in, out]` Parametru metody, které jsou zadané v obou *pInSignature* a *pOutSignature* objekty mají různé kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="a6546-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="a6546-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="a6546-125">0x80041036</span></span> | <span data-ttu-id="a6546-126">Chybí parametr metody specifikaci **ID** kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="a6546-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="a6546-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="a6546-127">0x80041038</span></span> | <span data-ttu-id="a6546-128">ID řady, která je přiřazena k parametrům metody není po sobě jdoucích nebo se nespustí na 0.</span><span class="sxs-lookup"><span data-stu-id="a6546-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="a6546-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="a6546-129">0x80041039</span></span> | <span data-ttu-id="a6546-130">Návratovou hodnotu pro metodu má **ID** kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="a6546-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="a6546-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="a6546-131">0x80041034</span></span> | <span data-ttu-id="a6546-132">Došlo k pokusu o opakované použití existujícího názvu metody od nadřazené třídy a podpisů se neshoduje.</span><span class="sxs-lookup"><span data-stu-id="a6546-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a6546-133">0</span><span class="sxs-lookup"><span data-stu-id="a6546-133">0</span></span> | <span data-ttu-id="a6546-134">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a6546-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a6546-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6546-135">Remarks</span></span>

<span data-ttu-id="a6546-136">Tato funkce zabalí volání [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="a6546-136">This function wraps a call to the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a6546-137">Toto volání metody je podporována pouze v případě `ptr` je definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="a6546-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="a6546-138">Manipulace s metoda není k dispozici z [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) ukazatele, které odkazují na modelu CIM instancí.</span><span class="sxs-lookup"><span data-stu-id="a6546-138">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) pointers that point to CIM instances.</span></span>

<span data-ttu-id="a6546-139">Uživatele nelze vytvořit metody s názvy, které začínat ani končit znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="a6546-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="a6546-140">Toto je vyhrazená pro systém třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a6546-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="a6546-141">Pro metodu `in` a `out` parametry jsou popsané v jako vlastnosti [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objekty.</span><span class="sxs-lookup"><span data-stu-id="a6546-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396) objects.</span></span>

<span data-ttu-id="a6546-142">`[in/out]` Parametr lze definovat přidáním stejnou vlastnost na oba objekty, na kterou odkazuje `pInSignature` a `pOutSignature` parametry.</span><span class="sxs-lookup"><span data-stu-id="a6546-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="a6546-143">V takovém případě vlastnosti sdílet stejný **ID** kvalifikátor hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a6546-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="a6546-144">Každou vlastnost v [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) třídy objektu jiné než `ReturnValue` musí mít **ID** kvalifikátor, počítáno od nuly číselnou hodnotu, která identifikuje pořadí, ve kterém se zobrazí parametry.</span><span class="sxs-lookup"><span data-stu-id="a6546-144">Each property in a [__Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="a6546-145">Žádné dva parametry může mít stejný **ID** hodnota a ne **ID** hodnoty mohou být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="a6546-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="a6546-146">Pokud dojde k buď podmínky, `PutMethod` funkce vrátí `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="a6546-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="a6546-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6546-147">Example</span></span>

<span data-ttu-id="a6546-148">Příklad, naleznete v části [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="a6546-148">For an example, see the [IWbemClassObject::PutMethod](https://msdn.microsoft.com/library/aa391456(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6546-149">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6546-149">Requirements</span></span>  
 <span data-ttu-id="a6546-150">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6546-150">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6546-151">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a6546-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a6546-152">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6546-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6546-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6546-153">See also</span></span>  
[<span data-ttu-id="a6546-154">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a6546-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
