---
title: PutMethod – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127334"
---
# <a name="putmethod-function"></a><span data-ttu-id="70949-103">PutMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="70949-103">PutMethod function</span></span>
<span data-ttu-id="70949-104">Vytvoří metodu.</span><span class="sxs-lookup"><span data-stu-id="70949-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="70949-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70949-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="70949-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70949-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="70949-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="70949-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="70949-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="70949-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="70949-109">pro Název metody, která se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="70949-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="70949-110">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="70949-110">[in] Reserved.</span></span> <span data-ttu-id="70949-111">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="70949-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="70949-112">pro Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje parametry `in` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="70949-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="70949-113">Tento parametr je ignorován, pokud je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="70949-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="70949-114">pro  Ukazatel na kopii [systémové třídy __Parameters](/windows/desktop/WmiSdk/--parameters) , která obsahuje parametry `out` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="70949-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="70949-115">Tento parametr je ignorován, pokud je nastavena na `null`.</span><span class="sxs-lookup"><span data-stu-id="70949-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="70949-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70949-116">Return value</span></span>

<span data-ttu-id="70949-117">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="70949-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="70949-118">Konstanta</span><span class="sxs-lookup"><span data-stu-id="70949-118">Constant</span></span>  |<span data-ttu-id="70949-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70949-119">Value</span></span>  |<span data-ttu-id="70949-120">Popis</span><span class="sxs-lookup"><span data-stu-id="70949-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="70949-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="70949-121">0x80041008</span></span> | <span data-ttu-id="70949-122">Jeden nebo více parametrů je neplatných.</span><span class="sxs-lookup"><span data-stu-id="70949-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="70949-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="70949-123">0x80041043</span></span> | <span data-ttu-id="70949-124">Parametr metody `[in, out]` zadaný v objektech *pInSignature* i *pOutSignature* mají různé kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="70949-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="70949-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="70949-125">0x80041036</span></span> | <span data-ttu-id="70949-126">V parametru metody chybí specifikace kvalifikátoru **ID** .</span><span class="sxs-lookup"><span data-stu-id="70949-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="70949-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="70949-127">0x80041038</span></span> | <span data-ttu-id="70949-128">Série ID, která je přiřazena parametrům metody, není po sobě, nebo nezačíná na 0.</span><span class="sxs-lookup"><span data-stu-id="70949-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="70949-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="70949-129">0x80041039</span></span> | <span data-ttu-id="70949-130">Návratová hodnota pro metodu má kvalifikátor **ID** .</span><span class="sxs-lookup"><span data-stu-id="70949-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="70949-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="70949-131">0x80041034</span></span> | <span data-ttu-id="70949-132">Došlo k pokusu o opětovné použití existujícího názvu metody z nadřazené třídy, přičemž signatury se neshodují.</span><span class="sxs-lookup"><span data-stu-id="70949-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="70949-133">0,8</span><span class="sxs-lookup"><span data-stu-id="70949-133">0</span></span> | <span data-ttu-id="70949-134">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="70949-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="70949-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70949-135">Remarks</span></span>

<span data-ttu-id="70949-136">Tato funkce zalomí volání metody [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="70949-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="70949-137">Toto volání metody je podporováno pouze v případě, `ptr` je definice třídy CIM.</span><span class="sxs-lookup"><span data-stu-id="70949-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="70949-138">Manipulace s metodou není k dispozici z ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) odkazujících na instance CIM.</span><span class="sxs-lookup"><span data-stu-id="70949-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="70949-139">Uživatelé nemůžou vytvářet metody s názvy, které začínají nebo končí podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="70949-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="70949-140">Toto je vyhrazeno pro systémové třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70949-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="70949-141">V případě metody jsou parametry `in` a `out` popsány jako vlastnosti v objektech [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="70949-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="70949-142">Parametr `[in/out]` lze definovat přidáním stejné vlastnosti do obou objektů, na které odkazují parametry `pInSignature` a `pOutSignature`.</span><span class="sxs-lookup"><span data-stu-id="70949-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="70949-143">V takovém případě vlastnosti sdílejí stejnou hodnotu kvalifikátoru **ID** .</span><span class="sxs-lookup"><span data-stu-id="70949-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="70949-144">Každá vlastnost v jiném objektu třídy [__Parameters](/windows/desktop/WmiSdk/--parameters) , než `ReturnValue`, musí mít kvalifikátor **ID** , číselnou hodnotu s nulovou hodnotou, která určuje pořadí, ve kterém se budou parametry zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="70949-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="70949-145">Žádné dva parametry nemohou mít stejnou hodnotu **ID** a žádná hodnota **ID** nemůže být vynechána.</span><span class="sxs-lookup"><span data-stu-id="70949-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="70949-146">Pokud dojde k oběma podmínkám, funkce `PutMethod` vrátí `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="70949-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="70949-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="70949-147">Example</span></span>

<span data-ttu-id="70949-148">Příklad naleznete v tématu metoda [IWbemclassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="70949-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70949-149">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70949-149">Requirements</span></span>  
 <span data-ttu-id="70949-150">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70949-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70949-151">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="70949-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="70949-152">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="70949-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70949-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70949-153">See also</span></span>

- [<span data-ttu-id="70949-154">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="70949-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
