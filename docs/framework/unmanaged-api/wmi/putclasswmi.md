---
title: "Funkce PutClassWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje stávající."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dda7dc4d71b65c8b031f2dca459bd282eef1f270
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="c3eb3-103">PutClassWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="c3eb3-103">PutClassWmi function</span></span>
<span data-ttu-id="c3eb3-104">Vytvoří novou třídu nebo aktualizuje stávající.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c3eb3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3eb3-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="c3eb3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3eb3-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="c3eb3-107">[v] Ukazatel na definici platnou třídu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="c3eb3-108">Je nutné správně inicializovat hodnoty všech požadovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="c3eb3-109">[v] Kombinace příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="c3eb3-110">Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="c3eb3-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="c3eb3-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="c3eb3-111">Constant</span></span>  |<span data-ttu-id="c3eb3-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3eb3-112">Value</span></span>  |<span data-ttu-id="c3eb3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c3eb3-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="c3eb3-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="c3eb3-114">0x20000</span></span> | <span data-ttu-id="c3eb3-115">Pokud sadu rozhraní WMI nejsou uložené žádné kvalifikátory s změněné příchuť.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="c3eb3-116">Není-li sadu, se předpokládá, že není lokalizované tento objekt a všechny kvalifikátory jsou storedwith této instance.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="c3eb3-117">0</span><span class="sxs-lookup"><span data-stu-id="c3eb3-117">0</span></span> | <span data-ttu-id="c3eb3-118">Vytvořte třídu, pokud ji neexistuje, nebo ho přepíše, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="c3eb3-119">1</span><span class="sxs-lookup"><span data-stu-id="c3eb3-119">1</span></span> | <span data-ttu-id="c3eb3-120">Aktualizace třídy.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-120">Update the class.</span></span> <span data-ttu-id="c3eb3-121">Třída musí existovat volání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="c3eb3-122">2</span><span class="sxs-lookup"><span data-stu-id="c3eb3-122">2</span></span> | <span data-ttu-id="c3eb3-123">Vytvořte třídu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-123">Create the class.</span></span> <span data-ttu-id="c3eb3-124">Volání selže, pokud třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="c3eb3-125">0x10</span><span class="sxs-lookup"><span data-stu-id="c3eb3-125">0x10</span></span> | <span data-ttu-id="c3eb3-126">Příznak způsobí, že polosynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="c3eb3-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="c3eb3-127">0x10000</span></span> | <span data-ttu-id="c3eb3-128">Zprostředkovatelé nabízené musíte zadat Tento příznak při volání metody `PutClassWmi` indikující, že tato třída se změnila.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="c3eb3-129">0</span><span class="sxs-lookup"><span data-stu-id="c3eb3-129">0</span></span> | <span data-ttu-id="c3eb3-130">Umožňuje aktualizovat, pokud nejsou žádné odvozené třídy a žádné instance této třídy třídu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="c3eb3-131">Také umožňuje provést aktualizace ve všech případech, pokud tato změna se používá pouze pro důležitý kvalifikátory, například popis kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="c3eb3-132">Pokud existuje instance dané třídy nebo změny mají důležité kvalifikátory, že se aktualizace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="c3eb3-133">0x20</span><span class="sxs-lookup"><span data-stu-id="c3eb3-133">0x20</span></span> | <span data-ttu-id="c3eb3-134">Umožňuje aktualizaci tříd, i když jsou podřízené třídy tak dlouho, dokud změnu nezpůsobí případné konflikty s podřízenými třídami.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="c3eb3-135">Tento příznak umožňuje například novou vlastnost být přidán do základní třídy, která nebyla dosud v některém z podřízené třídy.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="c3eb3-136">Pokud existuje instance dané třídy, že se aktualizace nezdaří.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="c3eb3-137">0x40</span><span class="sxs-lookup"><span data-stu-id="c3eb3-137">0x40</span></span> | <span data-ttu-id="c3eb3-138">vynutí aktualizaci tříd, pokud existuje konflikt s podřízenými třídami.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="c3eb3-139">Tento příznak například vynutí aktualizaci, když třída kvalifikátor je definována v podřízené třídy a základní třídy se pokusí přidat stejné kvalifikátor, který je v konfliktu s existující jeden thte.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="c3eb3-140">V režimu force tis konflikt vyřešit odstraněním konfliktní kvalifikátor ve třídě podřízené.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="c3eb3-141">[v] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="c3eb3-142">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="c3eb3-143">[out] Pokud `null`, tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="c3eb3-144">Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí okamžitě s `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="c3eb3-145">`ppCallResult` Parametr obdrží ukazatel na novou [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objektu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3eb3-146">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3eb3-146">Return value</span></span>

<span data-ttu-id="c3eb3-147">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="c3eb3-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c3eb3-148">Konstanta</span><span class="sxs-lookup"><span data-stu-id="c3eb3-148">Constant</span></span>  |<span data-ttu-id="c3eb3-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3eb3-149">Value</span></span>  |<span data-ttu-id="c3eb3-150">Popis</span><span class="sxs-lookup"><span data-stu-id="c3eb3-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="c3eb3-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="c3eb3-151">0x80041003</span></span> | <span data-ttu-id="c3eb3-152">Uživatel nemá oprávnění k vytvoření nebo úpravě třídy.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="c3eb3-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c3eb3-153">0x80041001</span></span> | <span data-ttu-id="c3eb3-154">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="c3eb3-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="c3eb3-155">0x80041010</span></span> | <span data-ttu-id="c3eb3-156">Zadaná třída není platná.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-156">The specified class is not valid.</span></span> <span data-ttu-id="c3eb3-157">Obvykle, znamená to, že `pObject` určuje instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c3eb3-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c3eb3-158">0x80041008</span></span> | <span data-ttu-id="c3eb3-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="c3eb3-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c3eb3-160">0x80041016</span></span> | <span data-ttu-id="c3eb3-161">Zadaná třída název je neplatný.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="c3eb3-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="c3eb3-162">0x80041025</span></span> | <span data-ttu-id="c3eb3-163">Došlo pokusu o provedení změny, které by způsobily neplatnost podtřídy.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="c3eb3-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="c3eb3-164">0x80041019</span></span> | <span data-ttu-id="c3eb3-165">`WBEM_FLAG_CREATE_ONLY` Byl zadán příznak, ale třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="c3eb3-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c3eb3-166">0x80041002</span></span> | <span data-ttu-id="c3eb3-167">`WBEM_FLAG_UPDATE_ONLY`byl zadán v `lFlags`, a třída nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="c3eb3-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="c3eb3-168">0x80041020</span></span> | <span data-ttu-id="c3eb3-169">Požadované vlastnosti pro třídy, ne všechny byly nastaveny.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c3eb3-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c3eb3-170">0x80041006</span></span> | <span data-ttu-id="c3eb3-171">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="c3eb3-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="c3eb3-172">0x80041033</span></span> | <span data-ttu-id="c3eb3-173">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="c3eb3-174">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="c3eb3-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="c3eb3-175">0x80041015</span></span> | <span data-ttu-id="c3eb3-176">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c3eb3-177">0</span><span class="sxs-lookup"><span data-stu-id="c3eb3-177">0</span></span> | <span data-ttu-id="c3eb3-178">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c3eb3-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3eb3-179">Remarks</span></span>

<span data-ttu-id="c3eb3-180">Tato funkce zabalí volání [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c3eb3-181">Uživatel nemusí vytvoření třídy s názvy, které začínat ani končit chacater podtržítko</span><span class="sxs-lookup"><span data-stu-id="c3eb3-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="c3eb3-182">Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="c3eb3-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3eb3-183">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3eb3-183">Requirements</span></span>  
 <span data-ttu-id="c3eb3-184">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3eb3-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3eb3-185">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c3eb3-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c3eb3-186">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c3eb3-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3eb3-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3eb3-187">See also</span></span>  
[<span data-ttu-id="c3eb3-188">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="c3eb3-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
