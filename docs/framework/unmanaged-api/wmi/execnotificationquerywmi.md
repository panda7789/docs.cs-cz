---
title: Funkce ExecNotificationQueryWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ExecNotificationQueryWmi provede dotaz přijímat události.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cac00ff96d0c7007bdd6135282c3f767217385e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935613"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="adc0e-103">Funkce ExecNotificationQueryWmi</span><span class="sxs-lookup"><span data-stu-id="adc0e-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="adc0e-104">Provede dotaz přijímat události.</span><span class="sxs-lookup"><span data-stu-id="adc0e-104">Executes a query to receive events.</span></span> <span data-ttu-id="adc0e-105">Volání se vrátí okamžitě a volající může dotazovat vrácené enumerátor pro události při jejich doručení.</span><span class="sxs-lookup"><span data-stu-id="adc0e-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="adc0e-106">Uvolnění vrácené enumerátor zruší dotazu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="adc0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc0e-107">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="adc0e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="adc0e-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="adc0e-109">[in] Řetězec s platnou dotazovací jazyk Windows Management podporuje.</span><span class="sxs-lookup"><span data-stu-id="adc0e-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="adc0e-110">Musí být "WQL", používá zkratka dotazovacího jazyka rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="adc0e-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="adc0e-111">[in] Text dotazu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-111">[in] The text of the query.</span></span> <span data-ttu-id="adc0e-112">Tento parametr nemůže mít `null`.</span><span class="sxs-lookup"><span data-stu-id="adc0e-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="adc0e-113">[in] Kombinace následující dva příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="adc0e-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="adc0e-114">Tyto hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="adc0e-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="adc0e-115">Constant</span></span> | <span data-ttu-id="adc0e-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="adc0e-116">Value</span></span>  | <span data-ttu-id="adc0e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="adc0e-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="adc0e-118">0x10</span><span class="sxs-lookup"><span data-stu-id="adc0e-118">0x10</span></span> | <span data-ttu-id="adc0e-119">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="adc0e-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="adc0e-120">Pokud není tento příznak nastaven, volání selže.</span><span class="sxs-lookup"><span data-stu-id="adc0e-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="adc0e-121">Je to proto průběžně přijetí události to znamená, že uživatel se musí dotazovat vrácené enumerátor.</span><span class="sxs-lookup"><span data-stu-id="adc0e-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="adc0e-122">Po neomezenou dobu blokování toto volání, který je nemožné.</span><span class="sxs-lookup"><span data-stu-id="adc0e-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="adc0e-123">0x20</span><span class="sxs-lookup"><span data-stu-id="adc0e-123">0x20</span></span> | <span data-ttu-id="adc0e-124">Vrátí enumerátor pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="adc0e-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="adc0e-125">Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="adc0e-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="adc0e-126">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="adc0e-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="adc0e-127">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované události.</span><span class="sxs-lookup"><span data-stu-id="adc0e-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="adc0e-128">[out] Pokud nenastane žádná chyba přijímá ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="adc0e-129">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="adc0e-130">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="adc0e-131">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="adc0e-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="adc0e-132">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="adc0e-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="adc0e-133">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="adc0e-133">[in] The user name.</span></span> <span data-ttu-id="adc0e-134">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="adc0e-135">[in] Heslo.</span><span class="sxs-lookup"><span data-stu-id="adc0e-135">[in] The password.</span></span> <span data-ttu-id="adc0e-136">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="adc0e-137">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="adc0e-137">[in] The domain name of the user.</span></span> <span data-ttu-id="adc0e-138">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="adc0e-139">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="adc0e-139">Return value</span></span>

<span data-ttu-id="adc0e-140">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="adc0e-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="adc0e-141">Konstanta</span><span class="sxs-lookup"><span data-stu-id="adc0e-141">Constant</span></span>  |<span data-ttu-id="adc0e-142">Value</span><span class="sxs-lookup"><span data-stu-id="adc0e-142">Value</span></span>  |<span data-ttu-id="adc0e-143">Popis</span><span class="sxs-lookup"><span data-stu-id="adc0e-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="adc0e-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="adc0e-144">0x80041003</span></span> | <span data-ttu-id="adc0e-145">Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které funkce může vrátit.</span><span class="sxs-lookup"><span data-stu-id="adc0e-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="adc0e-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="adc0e-146">0x80041001</span></span> | <span data-ttu-id="adc0e-147">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="adc0e-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="adc0e-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="adc0e-148">0x80041008</span></span> | <span data-ttu-id="adc0e-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="adc0e-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="adc0e-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="adc0e-150">0x80041010</span></span> | <span data-ttu-id="adc0e-151">Dotaz Určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="adc0e-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="adc0e-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="adc0e-152">0x80042002</span></span> | <span data-ttu-id="adc0e-153">Příliš mnoho přesnost při doručování událostí, které se požaduje.</span><span class="sxs-lookup"><span data-stu-id="adc0e-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="adc0e-154">Je třeba zadat větší tolerance cyklického dotazování.</span><span class="sxs-lookup"><span data-stu-id="adc0e-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="adc0e-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="adc0e-155">0x80042001</span></span> | <span data-ttu-id="adc0e-156">Dotaz požaduje více informací, než může poskytnout správy Windows.</span><span class="sxs-lookup"><span data-stu-id="adc0e-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="adc0e-157">To `HRESULT` je vrácena, když dotaz události výsledkem požadavku dotazování všechny objekty v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="adc0e-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="adc0e-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="adc0e-158">0x80041017</span></span> | <span data-ttu-id="adc0e-159">Dotazu došlo k chybě syntaxe.</span><span class="sxs-lookup"><span data-stu-id="adc0e-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="adc0e-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="adc0e-160">0x80041018</span></span> | <span data-ttu-id="adc0e-161">Požadovaný jazyk dotazu není podporován.</span><span class="sxs-lookup"><span data-stu-id="adc0e-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="adc0e-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="adc0e-162">0x8004106c</span></span> | <span data-ttu-id="adc0e-163">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="adc0e-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="adc0e-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="adc0e-164">0x80041006</span></span> | <span data-ttu-id="adc0e-165">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="adc0e-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="adc0e-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="adc0e-166">0x80041033</span></span> | <span data-ttu-id="adc0e-167">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="adc0e-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="adc0e-168">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="adc0e-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="adc0e-169">0x80041015</span></span> | <span data-ttu-id="adc0e-170">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="adc0e-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="adc0e-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="adc0e-171">0x80041058</span></span> | <span data-ttu-id="adc0e-172">Dotaz nelze parsovat.</span><span class="sxs-lookup"><span data-stu-id="adc0e-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="adc0e-173">0</span><span class="sxs-lookup"><span data-stu-id="adc0e-173">0</span></span> | <span data-ttu-id="adc0e-174">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="adc0e-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="adc0e-175">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adc0e-175">Remarks</span></span>

<span data-ttu-id="adc0e-176">Tato funkce zalamuje volání na [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) metody.</span><span class="sxs-lookup"><span data-stu-id="adc0e-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="adc0e-177">Po vrácení funkce volající předá pravidelně vráceného `ppEnum` objektu [Další](next.md) funkcí, pokud jsou k dispozici žádné události.</span><span class="sxs-lookup"><span data-stu-id="adc0e-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="adc0e-178">Existují omezení počtu `AND` a `OR` klíčová slova, které lze použít v dotazech WQL.</span><span class="sxs-lookup"><span data-stu-id="adc0e-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="adc0e-179">Velký počet klíčových slov jazyka WQL použit ve složitých dotazů může způsobit rozhraní WMI se vraťte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="adc0e-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="adc0e-180">Limit klíčová slova jazyka WQL závisí na tom, jak složitá je dotaz.</span><span class="sxs-lookup"><span data-stu-id="adc0e-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="adc0e-181">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="adc0e-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="adc0e-182">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adc0e-182">Requirements</span></span>

<span data-ttu-id="adc0e-183">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc0e-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="adc0e-184">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="adc0e-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="adc0e-185">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="adc0e-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="adc0e-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adc0e-186">See also</span></span>

- [<span data-ttu-id="adc0e-187">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="adc0e-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)