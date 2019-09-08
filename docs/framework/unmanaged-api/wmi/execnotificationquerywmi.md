---
title: ExecNotificationQueryWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce ExecNotificationQueryWmi spustí dotaz pro příjem událostí.
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
ms.openlocfilehash: 5cfe54c7c9b7ae707b2d3591afbd830bac171f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798642"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="1190a-103">Funkce ExecNotificationQueryWmi</span><span class="sxs-lookup"><span data-stu-id="1190a-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="1190a-104">Spustí dotaz pro příjem událostí.</span><span class="sxs-lookup"><span data-stu-id="1190a-104">Executes a query to receive events.</span></span> <span data-ttu-id="1190a-105">Volání se okamžitě vrátí a volající se může dotazovat vráceného enumerátoru na události při jejich doručení.</span><span class="sxs-lookup"><span data-stu-id="1190a-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="1190a-106">Uvolnění vráceného enumerátoru zruší dotaz.</span><span class="sxs-lookup"><span data-stu-id="1190a-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1190a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1190a-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="1190a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1190a-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="1190a-109">pro Řetězec s platným dotazovacím jazykem, který podporuje Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1190a-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="1190a-110">Musí být "WQL", zkratka pro jazyk WQL (WMI Query Language).</span><span class="sxs-lookup"><span data-stu-id="1190a-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="1190a-111">pro Text dotazu</span><span class="sxs-lookup"><span data-stu-id="1190a-111">[in] The text of the query.</span></span> <span data-ttu-id="1190a-112">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="1190a-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="1190a-113">pro Kombinace následujících dvou příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="1190a-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="1190a-114">Tyto hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete v kódu definovat jako konstanty.</span><span class="sxs-lookup"><span data-stu-id="1190a-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="1190a-115">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1190a-115">Constant</span></span> | <span data-ttu-id="1190a-116">Value</span><span class="sxs-lookup"><span data-stu-id="1190a-116">Value</span></span>  | <span data-ttu-id="1190a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1190a-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="1190a-118">0x10</span><span class="sxs-lookup"><span data-stu-id="1190a-118">0x10</span></span> | <span data-ttu-id="1190a-119">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="1190a-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="1190a-120">Pokud tento příznak není nastaven, volání se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="1190a-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="1190a-121">Důvodem je to, že události jsou průběžně přijímány, což znamená, že uživatel musí dotazovat vrácený enumerátor.</span><span class="sxs-lookup"><span data-stu-id="1190a-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="1190a-122">Blokování tohoto volání je neomezeně.</span><span class="sxs-lookup"><span data-stu-id="1190a-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="1190a-123">0x20</span><span class="sxs-lookup"><span data-stu-id="1190a-123">0x20</span></span> | <span data-ttu-id="1190a-124">Funkce vrátí enumerátor pouze s dopředné.</span><span class="sxs-lookup"><span data-stu-id="1190a-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="1190a-125">Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="1190a-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="1190a-126">pro Obvykle je `null`tato hodnota.</span><span class="sxs-lookup"><span data-stu-id="1190a-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="1190a-127">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované události.</span><span class="sxs-lookup"><span data-stu-id="1190a-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="1190a-128">mimo Pokud nedojde k žádné chybě, přijme ukazatel na enumerátor, který umožňuje volajícímu načíst instance v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="1190a-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="1190a-129">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="1190a-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="1190a-130">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="1190a-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="1190a-131">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="1190a-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="1190a-132">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1190a-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="1190a-133">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="1190a-133">[in] The user name.</span></span> <span data-ttu-id="1190a-134">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="1190a-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="1190a-135">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="1190a-135">[in] The password.</span></span> <span data-ttu-id="1190a-136">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="1190a-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="1190a-137">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="1190a-137">[in] The domain name of the user.</span></span> <span data-ttu-id="1190a-138">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="1190a-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="1190a-139">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1190a-139">Return value</span></span>

<span data-ttu-id="1190a-140">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="1190a-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1190a-141">Konstanta</span><span class="sxs-lookup"><span data-stu-id="1190a-141">Constant</span></span>  |<span data-ttu-id="1190a-142">Value</span><span class="sxs-lookup"><span data-stu-id="1190a-142">Value</span></span>  |<span data-ttu-id="1190a-143">Popis</span><span class="sxs-lookup"><span data-stu-id="1190a-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="1190a-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="1190a-144">0x80041003</span></span> | <span data-ttu-id="1190a-145">Uživatel nemá oprávnění k zobrazení jedné nebo více tříd, které může funkce vracet.</span><span class="sxs-lookup"><span data-stu-id="1190a-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="1190a-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1190a-146">0x80041001</span></span> | <span data-ttu-id="1190a-147">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="1190a-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1190a-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1190a-148">0x80041008</span></span> | <span data-ttu-id="1190a-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="1190a-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="1190a-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="1190a-150">0x80041010</span></span> | <span data-ttu-id="1190a-151">Dotaz určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1190a-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="1190a-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="1190a-152">0x80042002</span></span> | <span data-ttu-id="1190a-153">Bylo vyžádáno příliš mnoho přesností v doručení událostí.</span><span class="sxs-lookup"><span data-stu-id="1190a-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="1190a-154">Je nutné zadat větší toleranci dotazování.</span><span class="sxs-lookup"><span data-stu-id="1190a-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="1190a-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="1190a-155">0x80042001</span></span> | <span data-ttu-id="1190a-156">Dotaz vyžaduje více informací, než je Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1190a-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="1190a-157">To `HRESULT` se vrátí, když dotaz na událost má za následek požadavek na dotaz na všechny objekty v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1190a-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="1190a-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="1190a-158">0x80041017</span></span> | <span data-ttu-id="1190a-159">Dotaz obsahoval chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="1190a-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="1190a-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="1190a-160">0x80041018</span></span> | <span data-ttu-id="1190a-161">Požadovaný dotazovací jazyk není podporován.</span><span class="sxs-lookup"><span data-stu-id="1190a-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="1190a-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="1190a-162">0x8004106c</span></span> | <span data-ttu-id="1190a-163">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="1190a-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1190a-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1190a-164">0x80041006</span></span> | <span data-ttu-id="1190a-165">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="1190a-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="1190a-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="1190a-166">0x80041033</span></span> | <span data-ttu-id="1190a-167">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="1190a-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="1190a-168">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="1190a-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="1190a-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="1190a-169">0x80041015</span></span> | <span data-ttu-id="1190a-170">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="1190a-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="1190a-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="1190a-171">0x80041058</span></span> | <span data-ttu-id="1190a-172">Dotaz nelze analyzovat.</span><span class="sxs-lookup"><span data-stu-id="1190a-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1190a-173">0</span><span class="sxs-lookup"><span data-stu-id="1190a-173">0</span></span> | <span data-ttu-id="1190a-174">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="1190a-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1190a-175">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1190a-175">Remarks</span></span>

<span data-ttu-id="1190a-176">Tato funkce zalomí volání metody [Služby IWbem:: ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) .</span><span class="sxs-lookup"><span data-stu-id="1190a-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="1190a-177">Po návratu funkce volající pravidelně předává vráceného `ppEnum` objektu [Další](next.md) funkci, aby bylo možné zjistit, zda jsou k dispozici nějaké události.</span><span class="sxs-lookup"><span data-stu-id="1190a-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="1190a-178">Existují omezení pro počet `AND` a `OR` klíčová slova, která lze použít v dotazech jazyka WQL.</span><span class="sxs-lookup"><span data-stu-id="1190a-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="1190a-179">Velký počet klíčových slov jazyka WQL používaných ve složitých dotazech může způsobit, že `WBEM_E_QUOTA_VIOLATION` rozhraní WMI vrátí kód chyby (nebo 0x8004106c `HRESULT` ) jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1190a-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="1190a-180">Omezení klíčových slov jazyka WQL závisí na tom, jak je dotaz složitý.</span><span class="sxs-lookup"><span data-stu-id="1190a-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="1190a-181">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="1190a-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="1190a-182">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1190a-182">Requirements</span></span>

<span data-ttu-id="1190a-183">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1190a-183">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1190a-184">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1190a-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1190a-185">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1190a-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1190a-186">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1190a-186">See also</span></span>

- [<span data-ttu-id="1190a-187">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="1190a-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
