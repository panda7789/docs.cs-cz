---
title: "Funkce ExecNotificationQueryWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ExecNotificationQueryWmi provede dotaz přijímat události."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecNotificationQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecNotificationQueryWmi
helpviewer_keywords: ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f42878c146d478d5183342c3a743f3bd208008b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="b312d-103">ExecNotificationQueryWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="b312d-103">ExecNotificationQueryWmi function</span></span>
<span data-ttu-id="b312d-104">Provede dotaz přijímat události.</span><span class="sxs-lookup"><span data-stu-id="b312d-104">Executes a query to receive events.</span></span> <span data-ttu-id="b312d-105">Volání vrátí okamžitě a volající může dotazovat vrácený enumerátor pro události, když dorazí.</span><span class="sxs-lookup"><span data-stu-id="b312d-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="b312d-106">Uvolnění vrácený enumerátor zruší dotazu.</span><span class="sxs-lookup"><span data-stu-id="b312d-106">Releasing the returned enumerator cancels the query.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b312d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b312d-107">Syntax</span></span>  
  
```  
HRESULT ExecNotificationQueryWmi (
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

## <a name="parameters"></a><span data-ttu-id="b312d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="b312d-108">Parameters</span></span>

`strQueryLanguage`    
<span data-ttu-id="b312d-109">[v] Řetězec s platný dotaz jazyk podporovaný Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b312d-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="b312d-110">Musí být "WQL", zkratka pro rozhraní WMI Query Language.</span><span class="sxs-lookup"><span data-stu-id="b312d-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`  
<span data-ttu-id="b312d-111">[v] Text dotazu.</span><span class="sxs-lookup"><span data-stu-id="b312d-111">[in] The text of the query.</span></span> <span data-ttu-id="b312d-112">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="b312d-112">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="b312d-113">[v] Kombinace následující dvěma příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="b312d-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="b312d-114">Tyto hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty v kódu.</span><span class="sxs-lookup"><span data-stu-id="b312d-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> 

| <span data-ttu-id="b312d-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b312d-115">Constant</span></span> | <span data-ttu-id="b312d-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b312d-116">Value</span></span>  | <span data-ttu-id="b312d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b312d-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="b312d-118">0x10</span><span class="sxs-lookup"><span data-stu-id="b312d-118">0x10</span></span> | <span data-ttu-id="b312d-119">Příznak způsobí, že polosynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="b312d-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="b312d-120">Pokud není nastavený tento příznak, volání selže.</span><span class="sxs-lookup"><span data-stu-id="b312d-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="b312d-121">Je to proto události při přijetí nepřetržitě, což znamená, že uživatel musí dotazovat vrácený enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b312d-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="b312d-122">Po neomezenou dobu blokování toto volání provádí, které znemožňuje.</span><span class="sxs-lookup"><span data-stu-id="b312d-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="b312d-123">0x20</span><span class="sxs-lookup"><span data-stu-id="b312d-123">0x20</span></span> | <span data-ttu-id="b312d-124">Vrátí enumerátor dopředné.</span><span class="sxs-lookup"><span data-stu-id="b312d-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="b312d-125">Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md).</span><span class="sxs-lookup"><span data-stu-id="b312d-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`  
<span data-ttu-id="b312d-126">[v] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="b312d-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="b312d-127">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která mohou být využívána zprostředkovatele, který poskytuje požadovaný události.</span><span class="sxs-lookup"><span data-stu-id="b312d-127">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested events.</span></span> 

`ppEnum`  
<span data-ttu-id="b312d-128">[out] Pokud nedojde k žádné chybě, obdrží má ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="b312d-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="b312d-129">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="b312d-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`  
<span data-ttu-id="b312d-130">[v] Úroveň ověřování.</span><span class="sxs-lookup"><span data-stu-id="b312d-130">[in] The authorization level.</span></span>

<span data-ttu-id="b312d-131">`impLevel`[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="b312d-131">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="b312d-132">[v] Ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b312d-132">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="b312d-133">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="b312d-133">[in] The user name.</span></span> <span data-ttu-id="b312d-134">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="b312d-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="b312d-135">[v] Heslo.</span><span class="sxs-lookup"><span data-stu-id="b312d-135">[in] The password.</span></span> <span data-ttu-id="b312d-136">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="b312d-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="b312d-137">[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="b312d-137">[in] The domain name of the user.</span></span> <span data-ttu-id="b312d-138">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="b312d-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b312d-139">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b312d-139">Return value</span></span>

<span data-ttu-id="b312d-140">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="b312d-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b312d-141">Konstanta</span><span class="sxs-lookup"><span data-stu-id="b312d-141">Constant</span></span>  |<span data-ttu-id="b312d-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b312d-142">Value</span></span>  |<span data-ttu-id="b312d-143">Popis</span><span class="sxs-lookup"><span data-stu-id="b312d-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="b312d-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="b312d-144">0x80041003</span></span> | <span data-ttu-id="b312d-145">Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které můžou vrátit funkce.</span><span class="sxs-lookup"><span data-stu-id="b312d-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="b312d-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b312d-146">0x80041001</span></span> | <span data-ttu-id="b312d-147">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="b312d-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b312d-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b312d-148">0x80041008</span></span> | <span data-ttu-id="b312d-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="b312d-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="b312d-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="b312d-150">0x80041010</span></span> | <span data-ttu-id="b312d-151">Dotaz Určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="b312d-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="b312d-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="b312d-152">0x80042002</span></span> | <span data-ttu-id="b312d-153">Byla vyžádána příliš mnoho přesnost v doručení událostí.</span><span class="sxs-lookup"><span data-stu-id="b312d-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="b312d-154">Větší tolerance dotazování musí být zadán.</span><span class="sxs-lookup"><span data-stu-id="b312d-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="b312d-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="b312d-155">0x80042001</span></span> | <span data-ttu-id="b312d-156">Requess dotaz může poskytovat další informace než Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b312d-156">The query requess more information than Windows Management can provide.</span></span> <span data-ttu-id="b312d-157">To `HRESULT` je vrácena, pokud dotaz událostí výsledkem požadavku dotazování všechny objekty v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b312d-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="b312d-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="b312d-158">0x80041017</span></span> | <span data-ttu-id="b312d-159">Dotaz byl chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b312d-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="b312d-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="b312d-160">0x80041018</span></span> | <span data-ttu-id="b312d-161">Jazyk požadovaný dotaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="b312d-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="b312d-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="b312d-162">0x8004106c</span></span> | <span data-ttu-id="b312d-163">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="b312d-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b312d-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b312d-164">0x80041006</span></span> | <span data-ttu-id="b312d-165">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="b312d-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="b312d-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="b312d-166">0x80041033</span></span> | <span data-ttu-id="b312d-167">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="b312d-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="b312d-168">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="b312d-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b312d-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b312d-169">0x80041015</span></span> | <span data-ttu-id="b312d-170">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="b312d-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="b312d-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="b312d-171">0x80041058</span></span> | <span data-ttu-id="b312d-172">Dotaz nelze analyzovat.</span><span class="sxs-lookup"><span data-stu-id="b312d-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b312d-173">0</span><span class="sxs-lookup"><span data-stu-id="b312d-173">0</span></span> | <span data-ttu-id="b312d-174">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b312d-174">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b312d-175">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b312d-175">Remarks</span></span>

<span data-ttu-id="b312d-176">Tato funkce zabalí volání [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="b312d-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b312d-177">Po funkce vrátí hodnotu, volající předá pravidelně vrácený `ppEnum` do objektu [Další](next.md) funkce, které chcete zobrazit, pokud jsou k dispozici žádné události.</span><span class="sxs-lookup"><span data-stu-id="b312d-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="b312d-178">Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech WQL.</span><span class="sxs-lookup"><span data-stu-id="b312d-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="b312d-179">Velké počty klíčová slova jazyka WQL v dotazu komplexní může způsobit rozhraní WMI se vrátíte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b312d-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="b312d-180">Limit klíčová slova jazyka WQL, závisí na tom, jak složitá je dotaz.</span><span class="sxs-lookup"><span data-stu-id="b312d-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="b312d-181">Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b312d-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b312d-182">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b312d-182">Requirements</span></span>  
 <span data-ttu-id="b312d-183">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b312d-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b312d-184">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b312d-184">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b312d-185">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b312d-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b312d-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="b312d-186">See also</span></span>  
[<span data-ttu-id="b312d-187">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="b312d-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
