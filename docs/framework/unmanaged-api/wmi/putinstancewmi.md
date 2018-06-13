---
title: Funkce PutInstanceWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce PutInstanceWmi vytvoří nebo aktualizuje existující třídy instance.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db08ef4938a88ee657e2d65dda70edac09df8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462157"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="4fe7b-103">PutInstanceWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="4fe7b-103">PutInstanceWmi function</span></span>
<span data-ttu-id="4fe7b-104">Vytvoří nebo aktualizuje existující třídy instance.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="4fe7b-105">Instance je zapsán do úložiště služby WMI.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-105">The instance is written to the WMI repository.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4fe7b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe7b-106">Syntax</span></span>  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="4fe7b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fe7b-107">Parameters</span></span>

`pInst`    
<span data-ttu-id="4fe7b-108">[v] Ukazatel na instanci být writen.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-108">[in] A pointer to the instance to be writen.</span></span>

`lFlags`   
<span data-ttu-id="4fe7b-109">[v] Kombinace příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="4fe7b-110">Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="4fe7b-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="4fe7b-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4fe7b-111">Constant</span></span>  |<span data-ttu-id="4fe7b-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4fe7b-112">Value</span></span>  |<span data-ttu-id="4fe7b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe7b-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="4fe7b-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="4fe7b-114">0x20000</span></span> | <span data-ttu-id="4fe7b-115">Pokud nastavíte, rozhraní WMI nejsou uložené žádné kvalifikátory s **Amended** příchuť.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> </br> <span data-ttu-id="4fe7b-116">Není-li sadu, se předpokládá, že není lokalizované tento objekt a všechny kvalifikátory jsou storedwith této instance.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="4fe7b-117">0</span><span class="sxs-lookup"><span data-stu-id="4fe7b-117">0</span></span> | <span data-ttu-id="4fe7b-118">Vytvořte instanci, pokud ji neexistuje, nebo ho přepíše, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="4fe7b-119">1</span><span class="sxs-lookup"><span data-stu-id="4fe7b-119">1</span></span> | <span data-ttu-id="4fe7b-120">Aktualizace instance.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-120">Update the instance.</span></span> <span data-ttu-id="4fe7b-121">Instance musí existovat volání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="4fe7b-122">2</span><span class="sxs-lookup"><span data-stu-id="4fe7b-122">2</span></span> | <span data-ttu-id="4fe7b-123">Vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-123">Create the instance.</span></span> <span data-ttu-id="4fe7b-124">Volání selže, pokud instance již existuje.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="4fe7b-125">0x10</span><span class="sxs-lookup"><span data-stu-id="4fe7b-125">0x10</span></span> | <span data-ttu-id="4fe7b-126">Příznak způsobí, že polosynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`  
<span data-ttu-id="4fe7b-127">[v] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="4fe7b-128">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-128">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="4fe7b-129">[out] Pokud `null`, tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="4fe7b-130">Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí okamžitě s `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="4fe7b-131">`ppCallResult` Parametr obdrží ukazatel na novou [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objektu.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="4fe7b-132">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4fe7b-132">Return value</span></span>

<span data-ttu-id="4fe7b-133">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="4fe7b-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4fe7b-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4fe7b-134">Constant</span></span>  |<span data-ttu-id="4fe7b-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4fe7b-135">Value</span></span>  |<span data-ttu-id="4fe7b-136">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe7b-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="4fe7b-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="4fe7b-137">0x80041003</span></span> | <span data-ttu-id="4fe7b-138">Uživatel nemá oprávnění k aktualizaci instanci zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="4fe7b-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4fe7b-139">0x80041001</span></span> | <span data-ttu-id="4fe7b-140">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="4fe7b-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="4fe7b-141">0x80041010</span></span> | <span data-ttu-id="4fe7b-142">Třída podporuje tato instance není platný.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="4fe7b-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="4fe7b-143">0x80041028</span></span> | <span data-ttu-id="4fe7b-144">`null` zadaná pro vlastnost, která nemůže být `null`, například u takové, která je označena kvalifikátorem **indexované** nebo **Not_Null** kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="4fe7b-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="4fe7b-145">0x8004100f</span></span> | <span data-ttu-id="4fe7b-146">Zadaná instance není platný.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-146">The specified instance is not valid.</span></span> <span data-ttu-id="4fe7b-147">(Například volání `PutInstanceWmi` s třídou vrací hodnotu této.)</span><span class="sxs-lookup"><span data-stu-id="4fe7b-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4fe7b-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4fe7b-148">0x80041008</span></span> | <span data-ttu-id="4fe7b-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="4fe7b-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="4fe7b-150">0x80041019</span></span> | <span data-ttu-id="4fe7b-151">`WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, instance však již existuje.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="4fe7b-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="4fe7b-152">0x80041002</span></span> | <span data-ttu-id="4fe7b-153">`WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`, ale instance neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4fe7b-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4fe7b-154">0x80041006</span></span> | <span data-ttu-id="4fe7b-155">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="4fe7b-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="4fe7b-156">0x80041033</span></span> | <span data-ttu-id="4fe7b-157">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="4fe7b-158">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="4fe7b-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="4fe7b-159">0x80041015</span></span> | <span data-ttu-id="4fe7b-160">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="4fe7b-161">0</span><span class="sxs-lookup"><span data-stu-id="4fe7b-161">0</span></span> | <span data-ttu-id="4fe7b-162">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-162">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="4fe7b-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fe7b-163">Remarks</span></span>

<span data-ttu-id="4fe7b-164">Tato funkce zabalí volání [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-164">This function wraps a call to the [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4fe7b-165">`PutInstanceWmi` Funkce podporuje vytváření instancí a aktualizace instancí pouze existující třídy.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="4fe7b-166">V závislosti na tom, jak `pCtx` parametr je nastaven, jsou aktualizovány některé nebo všechny vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span> 

<span data-ttu-id="4fe7b-167">Pokud instance na kterou odkazuje `pInst` patří do podtřídy, Správa systému Windows volání všech poskytovatelů zodpovědná za třídy, ze kterých je odvozena podtřídy.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="4fe7b-168">Všechny tyto zprostředkovatele musí být úspěšně pro původní `PutInstanceWmi` žádost proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="4fe7b-169">Zprostředkovatel podpora nejhornější třídy v hierarchii jako první.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="4fe7b-170">Pořadí volání pokračuje podtřídou třídy nejhornější a pokračuje shora dolů, dokud nedosáhne Správa systému Windows zprostředkovatele pro třídu vlastnící instanci, na kterou odkazuje `pInst`.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="4fe7b-171">Správa systému Windows nevyvolá pro některý z podřízených tříd instance zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span> 

<span data-ttu-id="4fe7b-172">Když se aplikace musí aktualizace instanci, která patří do hierarchie tříd, `pInst` parametr musí odkazovat na instanci obsahující vlastnosti, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="4fe7b-173">To znamená, zvažte cílová instance, které patří do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="4fe7b-174">**ClassB** instance je odvozena z **ClassA**, a **ClassA** definuje vlastnost **PropA**.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="4fe7b-175">Pokud aplikace chce změňte na hodnotu **PropA** v **ClassB** instanci, je nutné nastavit `pInst` do této instance, a nikoli instanci **ClassA** .</span><span class="sxs-lookup"><span data-stu-id="4fe7b-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="4fe7b-176">Volání metody `PutInstanceWmi` v instanci abstraktní třídy není povoleno.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="4fe7b-177">Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="4fe7b-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="4fe7b-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fe7b-178">Requirements</span></span>  
 <span data-ttu-id="4fe7b-179">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe7b-179">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe7b-180">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4fe7b-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4fe7b-181">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe7b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe7b-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fe7b-182">See also</span></span>  
[<span data-ttu-id="4fe7b-183">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4fe7b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
