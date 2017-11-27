---
title: "Funkce ExecQueryWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ExecQueryWmi provede dotaz pro načtení objektů."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ebd5463fd3b4109203e829da8e3683bbb79cf59
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="execquerywmi-function"></a><span data-ttu-id="350c5-103">ExecQueryWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="350c5-103">ExecQueryWmi function</span></span>
<span data-ttu-id="350c5-104">Provede dotaz pro načtení objektů.</span><span class="sxs-lookup"><span data-stu-id="350c5-104">Executes a query to retrieve objects.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="350c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="350c5-105">Syntax</span></span>  
  
```  
HRESULT ExecQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a><span data-ttu-id="350c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="350c5-106">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="350c5-107">[v] Řetězec s platný dotaz jazyk podporovaný Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="350c5-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="350c5-108">Musí být "WQL", zkratka pro rozhraní WMI Query Language.</span><span class="sxs-lookup"><span data-stu-id="350c5-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="350c5-109">[v] Text dotazu.</span><span class="sxs-lookup"><span data-stu-id="350c5-109">[in] The text of the query.</span></span> <span data-ttu-id="350c5-110">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="350c5-110">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="350c5-111">[v] Kombinace příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="350c5-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="350c5-112">Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="350c5-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

| <span data-ttu-id="350c5-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="350c5-113">Constant</span></span> | <span data-ttu-id="350c5-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="350c5-114">Value</span></span>  | <span data-ttu-id="350c5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="350c5-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="350c5-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="350c5-116">0x20000</span></span> | <span data-ttu-id="350c5-117">Pokud sadu, funkce načte doplněné kvalifikátory uložené v lokalizovaných obor názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="350c5-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="350c5-118">Pokud není sada, funkce načte pouze kvalifikátory uložené v oboru názvů okamžitou.</span><span class="sxs-lookup"><span data-stu-id="350c5-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="350c5-119">0x10</span><span class="sxs-lookup"><span data-stu-id="350c5-119">0x10</span></span> | <span data-ttu-id="350c5-120">Příznak způsobí, že polosynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="350c5-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="350c5-121">0x20</span><span class="sxs-lookup"><span data-stu-id="350c5-121">0x20</span></span> | <span data-ttu-id="350c5-122">Vrátí enumerátor dopředné.</span><span class="sxs-lookup"><span data-stu-id="350c5-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="350c5-123">Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md).</span><span class="sxs-lookup"><span data-stu-id="350c5-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="350c5-124">0</span><span class="sxs-lookup"><span data-stu-id="350c5-124">0</span></span> | <span data-ttu-id="350c5-125">Rozhraní WMI zachová ukazatelé na objekty v enumration, dokud jejich vydání.</span><span class="sxs-lookup"><span data-stu-id="350c5-125">WMI retains pointers to objects in the enumration until they are released.</span></span> | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="350c5-126">0x100</span><span class="sxs-lookup"><span data-stu-id="350c5-126">0x100</span></span> | <span data-ttu-id="350c5-127">Zajišťuje, že všechny vrátí objekty mají dostatek informací v nich proto této vlastnosti systému, jako například **__PATH**, **__RELPATH**, a **__SERVER**, nejsou `null`.</span><span class="sxs-lookup"><span data-stu-id="350c5-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="350c5-128">2</span><span class="sxs-lookup"><span data-stu-id="350c5-128">2</span></span> | <span data-ttu-id="350c5-129">Tento příznak se používá pro při vytváření prototypu.</span><span class="sxs-lookup"><span data-stu-id="350c5-129">This flag is used for prototyping.</span></span> <span data-ttu-id="350c5-130">Ho nepracuje dotaz a místo toho vrátí objekt, který vypadá jako objekt obvykle za následek.</span><span class="sxs-lookup"><span data-stu-id="350c5-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="350c5-131">0x200</span><span class="sxs-lookup"><span data-stu-id="350c5-131">0x200</span></span> | <span data-ttu-id="350c5-132">Příčiny přímý přístup k poskytovateli pro zadaná třída bez ohledu na své nadřazené třídy nebo všechny podtřídy.</span><span class="sxs-lookup"><span data-stu-id="350c5-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="350c5-133">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="350c5-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="350c5-134">[v] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="350c5-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="350c5-135">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="350c5-135">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="350c5-136">[out] Pokud nedojde k žádné chybě, obdrží má ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="350c5-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="350c5-137">Dotaz může mít nulový počet instancí sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="350c5-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="350c5-138">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="350c5-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="350c5-139">[v] Úroveň ověřování.</span><span class="sxs-lookup"><span data-stu-id="350c5-139">[in] The authorization level.</span></span>

<span data-ttu-id="350c5-140">`impLevel`[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="350c5-140">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="350c5-141">[v] Ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="350c5-141">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="350c5-142">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="350c5-142">[in] The user name.</span></span> <span data-ttu-id="350c5-143">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="350c5-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="350c5-144">[v] Heslo.</span><span class="sxs-lookup"><span data-stu-id="350c5-144">[in] The password.</span></span> <span data-ttu-id="350c5-145">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="350c5-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="350c5-146">[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="350c5-146">[in] The domain name of the user.</span></span> <span data-ttu-id="350c5-147">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="350c5-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="350c5-148">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="350c5-148">Return value</span></span>

<span data-ttu-id="350c5-149">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="350c5-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="350c5-150">Konstanta</span><span class="sxs-lookup"><span data-stu-id="350c5-150">Constant</span></span>  |<span data-ttu-id="350c5-151">Hodnota</span><span class="sxs-lookup"><span data-stu-id="350c5-151">Value</span></span>  |<span data-ttu-id="350c5-152">Popis</span><span class="sxs-lookup"><span data-stu-id="350c5-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="350c5-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="350c5-153">0x80041003</span></span> | <span data-ttu-id="350c5-154">Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které můžou vrátit funkce.</span><span class="sxs-lookup"><span data-stu-id="350c5-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="350c5-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="350c5-155">0x80041001</span></span> | <span data-ttu-id="350c5-156">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="350c5-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="350c5-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="350c5-157">0x80041008</span></span> | <span data-ttu-id="350c5-158">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="350c5-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="350c5-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="350c5-159">0x80041017</span></span> | <span data-ttu-id="350c5-160">Dotaz byl chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="350c5-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="350c5-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="350c5-161">0x80041018</span></span> | <span data-ttu-id="350c5-162">Jazyk požadovaný dotaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="350c5-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="350c5-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="350c5-163">0x8004106c</span></span> | <span data-ttu-id="350c5-164">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="350c5-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="350c5-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="350c5-165">0x80041006</span></span> | <span data-ttu-id="350c5-166">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="350c5-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="350c5-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="350c5-167">0x80041033</span></span> | <span data-ttu-id="350c5-168">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="350c5-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="350c5-169">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="350c5-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="350c5-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="350c5-170">0x80041015</span></span> | <span data-ttu-id="350c5-171">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="350c5-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="350c5-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="350c5-172">0x80041002</span></span> | <span data-ttu-id="350c5-173">Dotaz Určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="350c5-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="350c5-174">0</span><span class="sxs-lookup"><span data-stu-id="350c5-174">0</span></span> | <span data-ttu-id="350c5-175">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="350c5-175">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="350c5-176">Poznámky</span><span class="sxs-lookup"><span data-stu-id="350c5-176">Remarks</span></span>

<span data-ttu-id="350c5-177">Tato funkce zabalí volání [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="350c5-177">This function wraps a call to the [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="350c5-178">Tato funkce zpracovává zadaný v dotazu `strQuery` parametr a vytvoří enumerátor, pomocí kterého můžete volající přístup výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="350c5-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="350c5-179">Enumerátor je ukazatel na [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) rozhraní; dotaz výsledky jsou instancemi třídy objektů, které jsou dostupné prostřednictvím [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="350c5-179">The enumerator is a pointer to an [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interface; the query results are instances of class objects made available through the [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interface.</span></span>

<span data-ttu-id="350c5-180">Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech WQL.</span><span class="sxs-lookup"><span data-stu-id="350c5-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="350c5-181">Velké počty klíčová slova jazyka WQL v dotazu komplexní může způsobit rozhraní WMI se vrátíte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="350c5-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="350c5-182">Limit klíčová slova jazyka WQL, závisí na tom, jak složitá je dotaz.</span><span class="sxs-lookup"><span data-stu-id="350c5-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="350c5-183">Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="350c5-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="350c5-184">Požadavky</span><span class="sxs-lookup"><span data-stu-id="350c5-184">Requirements</span></span>  
 <span data-ttu-id="350c5-185">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="350c5-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="350c5-186">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="350c5-186">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="350c5-187">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="350c5-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350c5-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="350c5-188">See also</span></span>  
[<span data-ttu-id="350c5-189">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="350c5-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
