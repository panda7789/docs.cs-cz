---
title: Funkce ExecQueryWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ExecQueryWmi spustí dotaz pro načtení objektů.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3db6ddf51b8e83635f594c4716b57551475dc96f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636585"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="e937c-103">Funkce ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="e937c-103">ExecQueryWmi function</span></span>

<span data-ttu-id="e937c-104">Spustí dotaz pro načtení objektů.</span><span class="sxs-lookup"><span data-stu-id="e937c-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e937c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e937c-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="e937c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e937c-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="e937c-107">[in] Řetězec s platnou dotazovací jazyk Windows Management podporuje.</span><span class="sxs-lookup"><span data-stu-id="e937c-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="e937c-108">Musí být "WQL", používá zkratka dotazovacího jazyka rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="e937c-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="e937c-109">[in] Text dotazu.</span><span class="sxs-lookup"><span data-stu-id="e937c-109">[in] The text of the query.</span></span> <span data-ttu-id="e937c-110">Tento parametr nemůže mít `null`.</span><span class="sxs-lookup"><span data-stu-id="e937c-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="e937c-111">[in] Kombinace příznaků, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="e937c-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="e937c-112">Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e937c-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="e937c-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e937c-113">Constant</span></span> | <span data-ttu-id="e937c-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e937c-114">Value</span></span>  | <span data-ttu-id="e937c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e937c-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="e937c-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="e937c-116">0x20000</span></span> | <span data-ttu-id="e937c-117">Pokud sada funkce načte upravenou kvalifikátory uložené v lokalizovaných názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="e937c-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="e937c-118">Pokud není sada, funkce načte jenom v kvalifikátorech uložené v oboru názvů okamžité.</span><span class="sxs-lookup"><span data-stu-id="e937c-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="e937c-119">0x10</span><span class="sxs-lookup"><span data-stu-id="e937c-119">0x10</span></span> | <span data-ttu-id="e937c-120">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="e937c-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="e937c-121">0x20</span><span class="sxs-lookup"><span data-stu-id="e937c-121">0x20</span></span> | <span data-ttu-id="e937c-122">Vrátí enumerátor pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="e937c-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="e937c-123">Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="e937c-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="e937c-124">0</span><span class="sxs-lookup"><span data-stu-id="e937c-124">0</span></span> | <span data-ttu-id="e937c-125">Rozhraní WMI uchovává ukazatelů na objekty ve výčtu, dokud se neuvolní.</span><span class="sxs-lookup"><span data-stu-id="e937c-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="e937c-126">0x100</span><span class="sxs-lookup"><span data-stu-id="e937c-126">0x100</span></span> | <span data-ttu-id="e937c-127">Zajišťuje, že některé vrátí objekty mají dostatek informací v nich tak této vlastnosti systému jako **__PATH**, **__RELPATH**, a **__SERVER**, nejsou `null`.</span><span class="sxs-lookup"><span data-stu-id="e937c-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="e937c-128">2</span><span class="sxs-lookup"><span data-stu-id="e937c-128">2</span></span> | <span data-ttu-id="e937c-129">Tento příznak se používá pro vytváření prototypů.</span><span class="sxs-lookup"><span data-stu-id="e937c-129">This flag is used for prototyping.</span></span> <span data-ttu-id="e937c-130">Nelze spustit dotaz a místo toho vrátí objekt, který vypadá jako obvykle za následek objektu.</span><span class="sxs-lookup"><span data-stu-id="e937c-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="e937c-131">0x200</span><span class="sxs-lookup"><span data-stu-id="e937c-131">0x200</span></span> | <span data-ttu-id="e937c-132">Způsobí, že přímý přístup k poskytovateli pro zadaný bez ohledu na jeho nadřazené třídu nebo jakékoli podtřídy třídy.</span><span class="sxs-lookup"><span data-stu-id="e937c-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="e937c-133">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro zajištění nejlepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="e937c-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="e937c-134">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="e937c-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="e937c-135">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="e937c-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="e937c-136">[out] Pokud nenastane žádná chyba přijímá ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="e937c-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="e937c-137">Dotaz může mít nula instancemi sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="e937c-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="e937c-138">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="e937c-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="e937c-139">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="e937c-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="e937c-140">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="e937c-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="e937c-141">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e937c-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="e937c-142">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="e937c-142">[in] The user name.</span></span> <span data-ttu-id="e937c-143">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="e937c-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="e937c-144">[in] Heslo.</span><span class="sxs-lookup"><span data-stu-id="e937c-144">[in] The password.</span></span> <span data-ttu-id="e937c-145">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="e937c-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="e937c-146">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="e937c-146">[in] The domain name of the user.</span></span> <span data-ttu-id="e937c-147">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="e937c-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="e937c-148">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e937c-148">Return value</span></span>

<span data-ttu-id="e937c-149">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="e937c-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e937c-150">Konstanta</span><span class="sxs-lookup"><span data-stu-id="e937c-150">Constant</span></span>  |<span data-ttu-id="e937c-151">Value</span><span class="sxs-lookup"><span data-stu-id="e937c-151">Value</span></span>  |<span data-ttu-id="e937c-152">Popis</span><span class="sxs-lookup"><span data-stu-id="e937c-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="e937c-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="e937c-153">0x80041003</span></span> | <span data-ttu-id="e937c-154">Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které funkce může vrátit.</span><span class="sxs-lookup"><span data-stu-id="e937c-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="e937c-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e937c-155">0x80041001</span></span> | <span data-ttu-id="e937c-156">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="e937c-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e937c-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e937c-157">0x80041008</span></span> | <span data-ttu-id="e937c-158">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="e937c-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="e937c-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="e937c-159">0x80041017</span></span> | <span data-ttu-id="e937c-160">Dotazu došlo k chybě syntaxe.</span><span class="sxs-lookup"><span data-stu-id="e937c-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="e937c-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="e937c-161">0x80041018</span></span> | <span data-ttu-id="e937c-162">Požadovaný jazyk dotazu není podporován.</span><span class="sxs-lookup"><span data-stu-id="e937c-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="e937c-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="e937c-163">0x8004106c</span></span> | <span data-ttu-id="e937c-164">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="e937c-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e937c-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e937c-165">0x80041006</span></span> | <span data-ttu-id="e937c-166">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="e937c-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="e937c-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="e937c-167">0x80041033</span></span> | <span data-ttu-id="e937c-168">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="e937c-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="e937c-169">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="e937c-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="e937c-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="e937c-170">0x80041015</span></span> | <span data-ttu-id="e937c-171">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="e937c-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="e937c-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e937c-172">0x80041002</span></span> | <span data-ttu-id="e937c-173">Dotaz Určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e937c-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e937c-174">0</span><span class="sxs-lookup"><span data-stu-id="e937c-174">0</span></span> | <span data-ttu-id="e937c-175">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e937c-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e937c-176">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e937c-176">Remarks</span></span>

<span data-ttu-id="e937c-177">Tato funkce zalamuje volání na [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) metody.</span><span class="sxs-lookup"><span data-stu-id="e937c-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="e937c-178">Tato funkce zpracuje dotaz zadaný v `strQuery` parametr a vytvoří čítač přes který může volající přístup výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="e937c-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="e937c-179">Enumerátor je ukazatel [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) rozhraní; dotaz výsledky jsou instance třídy objektů k dispozici prostřednictvím [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e937c-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="e937c-180">Existují omezení počtu `AND` a `OR` klíčová slova, které lze použít v dotazech WQL.</span><span class="sxs-lookup"><span data-stu-id="e937c-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="e937c-181">Velký počet klíčových slov jazyka WQL použit ve složitých dotazů může způsobit rozhraní WMI se vraťte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e937c-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="e937c-182">Limit klíčová slova jazyka WQL závisí na tom, jak složitá je dotaz.</span><span class="sxs-lookup"><span data-stu-id="e937c-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="e937c-183">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="e937c-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e937c-184">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e937c-184">Requirements</span></span>

<span data-ttu-id="e937c-185">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e937c-185">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e937c-186">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e937c-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e937c-187">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e937c-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e937c-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e937c-188">See also</span></span>

- [<span data-ttu-id="e937c-189">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="e937c-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
