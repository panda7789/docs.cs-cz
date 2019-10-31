---
title: ExecQueryWmi – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130438"
---
# <a name="execquerywmi-function"></a><span data-ttu-id="5560d-103">Funkce ExecQueryWmi</span><span class="sxs-lookup"><span data-stu-id="5560d-103">ExecQueryWmi function</span></span>

<span data-ttu-id="5560d-104">Spustí dotaz pro načtení objektů.</span><span class="sxs-lookup"><span data-stu-id="5560d-104">Executes a query to retrieve objects.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5560d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5560d-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="5560d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5560d-106">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="5560d-107">pro Řetězec s platným dotazovacím jazykem, který podporuje Správa systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5560d-107">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="5560d-108">Musí být "WQL", zkratka pro jazyk WQL (WMI Query Language).</span><span class="sxs-lookup"><span data-stu-id="5560d-108">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="5560d-109">pro Text dotazu</span><span class="sxs-lookup"><span data-stu-id="5560d-109">[in] The text of the query.</span></span> <span data-ttu-id="5560d-110">Tento parametr nelze `null`.</span><span class="sxs-lookup"><span data-stu-id="5560d-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="5560d-111">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="5560d-111">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5560d-112">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5560d-112">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

| <span data-ttu-id="5560d-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5560d-113">Constant</span></span> | <span data-ttu-id="5560d-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5560d-114">Value</span></span>  | <span data-ttu-id="5560d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5560d-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5560d-116">0x20000</span><span class="sxs-lookup"><span data-stu-id="5560d-116">0x20000</span></span> | <span data-ttu-id="5560d-117">Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="5560d-117">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="5560d-118">Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5560d-118">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5560d-119">0x10</span><span class="sxs-lookup"><span data-stu-id="5560d-119">0x10</span></span> | <span data-ttu-id="5560d-120">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="5560d-120">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="5560d-121">0x20</span><span class="sxs-lookup"><span data-stu-id="5560d-121">0x20</span></span> | <span data-ttu-id="5560d-122">Funkce vrátí enumerátor pouze s dopředné.</span><span class="sxs-lookup"><span data-stu-id="5560d-122">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="5560d-123">Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="5560d-123">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="5560d-124">0,8</span><span class="sxs-lookup"><span data-stu-id="5560d-124">0</span></span> | <span data-ttu-id="5560d-125">Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="5560d-125">WMI retains pointers to objects in the enumeration until they are released.</span></span> |
| `WBEM_FLAG_ENSURE_LOCATABLE` | <span data-ttu-id="5560d-126">0x100</span><span class="sxs-lookup"><span data-stu-id="5560d-126">0x100</span></span> | <span data-ttu-id="5560d-127">Zajistí, že všechny vrácené objekty mají v nich dostatek informací, aby nebyly `null`systémové vlastnosti, například **__PATH**, **__RELPATH**a **__SERVER**.</span><span class="sxs-lookup"><span data-stu-id="5560d-127">Ensures that any returned objects have enough information in them so that system properties, such as **__PATH**, **__RELPATH**, and **__SERVER**, are not `null`.</span></span> |
| `WBEM_FLAG_PROTOTYPE` | <span data-ttu-id="5560d-128">odst</span><span class="sxs-lookup"><span data-stu-id="5560d-128">2</span></span> | <span data-ttu-id="5560d-129">Tento příznak se používá pro vytváření prototypů.</span><span class="sxs-lookup"><span data-stu-id="5560d-129">This flag is used for prototyping.</span></span> <span data-ttu-id="5560d-130">Nespustí dotaz a místo toho vrátí objekt, který vypadá jako typický objekt výsledku.</span><span class="sxs-lookup"><span data-stu-id="5560d-130">It does not execute the query and instead returns an object that looks like a typical result object.</span></span> |
| `WBEM_FLAG_DIRECT_READ` | <span data-ttu-id="5560d-131">0x200</span><span class="sxs-lookup"><span data-stu-id="5560d-131">0x200</span></span> | <span data-ttu-id="5560d-132">Způsobuje přímý přístup k poskytovateli pro třídu určenou bez ohledu na její nadřazenou třídu nebo žádné podtřídy.</span><span class="sxs-lookup"><span data-stu-id="5560d-132">Causes direct access to the provider for the class specified without regard to its parent class or any subclasses.</span></span> |

<span data-ttu-id="5560d-133">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="5560d-133">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="5560d-134">pro Tato hodnota je obvykle `null`.</span><span class="sxs-lookup"><span data-stu-id="5560d-134">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5560d-135">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="5560d-135">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="5560d-136">mimo Pokud nedojde k žádné chybě, přijme ukazatel na enumerátor, který umožňuje volajícímu načíst instance v sadě výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="5560d-136">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="5560d-137">Dotaz může mít sadu výsledků s nulovými instancemi.</span><span class="sxs-lookup"><span data-stu-id="5560d-137">The query can have a result set with zero instances.</span></span> <span data-ttu-id="5560d-138">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="5560d-138">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="5560d-139">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="5560d-139">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="5560d-140">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="5560d-140">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="5560d-141">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5560d-141">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="5560d-142">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="5560d-142">[in] The user name.</span></span> <span data-ttu-id="5560d-143">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="5560d-143">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="5560d-144">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="5560d-144">[in] The password.</span></span> <span data-ttu-id="5560d-145">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="5560d-145">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="5560d-146">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="5560d-146">[in] The domain name of the user.</span></span> <span data-ttu-id="5560d-147">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="5560d-147">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5560d-148">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5560d-148">Return value</span></span>

<span data-ttu-id="5560d-149">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5560d-149">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5560d-150">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5560d-150">Constant</span></span>  |<span data-ttu-id="5560d-151">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5560d-151">Value</span></span>  |<span data-ttu-id="5560d-152">Popis</span><span class="sxs-lookup"><span data-stu-id="5560d-152">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5560d-153">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5560d-153">0x80041003</span></span> | <span data-ttu-id="5560d-154">Uživatel nemá oprávnění k zobrazení jedné nebo více tříd, které může funkce vracet.</span><span class="sxs-lookup"><span data-stu-id="5560d-154">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5560d-155">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5560d-155">0x80041001</span></span> | <span data-ttu-id="5560d-156">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="5560d-156">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5560d-157">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5560d-157">0x80041008</span></span> | <span data-ttu-id="5560d-158">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="5560d-158">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="5560d-159">0x80041017</span><span class="sxs-lookup"><span data-stu-id="5560d-159">0x80041017</span></span> | <span data-ttu-id="5560d-160">Dotaz obsahoval chybu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5560d-160">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="5560d-161">0x80041018</span><span class="sxs-lookup"><span data-stu-id="5560d-161">0x80041018</span></span> | <span data-ttu-id="5560d-162">Požadovaný dotazovací jazyk není podporován.</span><span class="sxs-lookup"><span data-stu-id="5560d-162">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="5560d-163">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="5560d-163">0x8004106c</span></span> | <span data-ttu-id="5560d-164">Dotaz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="5560d-164">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5560d-165">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5560d-165">0x80041006</span></span> | <span data-ttu-id="5560d-166">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="5560d-166">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5560d-167">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5560d-167">0x80041033</span></span> | <span data-ttu-id="5560d-168">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="5560d-168">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5560d-169">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="5560d-169">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5560d-170">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5560d-170">0x80041015</span></span> | <span data-ttu-id="5560d-171">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5560d-171">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="5560d-172">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5560d-172">0x80041002</span></span> | <span data-ttu-id="5560d-173">Dotaz určuje třídu, která neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5560d-173">The query specifies a class that does not exist.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5560d-174">0,8</span><span class="sxs-lookup"><span data-stu-id="5560d-174">0</span></span> | <span data-ttu-id="5560d-175">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5560d-175">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="5560d-176">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5560d-176">Remarks</span></span>

<span data-ttu-id="5560d-177">Tato funkce zalomí volání metody [Služby IWbem:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .</span><span class="sxs-lookup"><span data-stu-id="5560d-177">This function wraps a call to the [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) method.</span></span>

<span data-ttu-id="5560d-178">Tato funkce zpracuje dotaz zadaný v parametru `strQuery` a vytvoří enumerátor, přes který volající může získat přístup k výsledkům dotazu.</span><span class="sxs-lookup"><span data-stu-id="5560d-178">This function processes the query specified in the `strQuery` parameter and creates an enumerator through which the caller can access the query results.</span></span> <span data-ttu-id="5560d-179">Enumerátor je ukazatel na rozhraní [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; výsledky dotazu jsou instance objektů třídy, které jsou k dispozici prostřednictvím rozhraní [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="5560d-179">The enumerator is a pointer to an [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interface; the query results are instances of class objects made available through the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interface.</span></span>

<span data-ttu-id="5560d-180">Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech jazyka WQL.</span><span class="sxs-lookup"><span data-stu-id="5560d-180">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="5560d-181">Velký počet klíčových slov jazyka WQL používaných ve složitých dotazech může způsobit, že rozhraní WMI vrátí kód chyby `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) jako hodnotu `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5560d-181">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="5560d-182">Omezení klíčových slov jazyka WQL závisí na tom, jak je dotaz složitý.</span><span class="sxs-lookup"><span data-stu-id="5560d-182">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="5560d-183">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="5560d-183">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5560d-184">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5560d-184">Requirements</span></span>

<span data-ttu-id="5560d-185">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5560d-185">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5560d-186">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="5560d-186">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="5560d-187">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5560d-187">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5560d-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5560d-188">See also</span></span>

- [<span data-ttu-id="5560d-189">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5560d-189">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
