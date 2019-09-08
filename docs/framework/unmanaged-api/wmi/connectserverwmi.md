---
title: ConnectServerWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce ConnectServerWmi používá model DCOM k vytvoření připojení k oboru názvů rozhraní WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798749"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="aafa8-103">ConnectServerWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="aafa8-103">ConnectServerWmi function</span></span>

<span data-ttu-id="aafa8-104">Vytvoří připojení prostřednictvím modelu DCOM k oboru názvů WMI v zadaném počítači.</span><span class="sxs-lookup"><span data-stu-id="aafa8-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aafa8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aafa8-105">Syntax</span></span>

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a><span data-ttu-id="aafa8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aafa8-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="aafa8-107">pro Ukazatel na platný `BSTR` , který obsahuje cestu k objektu správného oboru názvů rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="aafa8-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="aafa8-108">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="aafa8-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="aafa8-109">pro Ukazatel na platný `BSTR` , který obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="aafa8-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="aafa8-110">`null` Hodnota označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aafa8-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="aafa8-111">Pokud uživatel pochází z jiné domény než z aktuální, `strUser` může také obsahovat doménu a uživatelské jméno oddělené zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="aafa8-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="aafa8-112">`strUser`může být také ve formátu hlavního názvu uživatele (UPN), například `userName@domainName`.</span><span class="sxs-lookup"><span data-stu-id="aafa8-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="aafa8-113">Další informace najdete v části [poznámky](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="aafa8-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="aafa8-114">pro Ukazatel na platný `BSTR` , který obsahuje heslo.</span><span class="sxs-lookup"><span data-stu-id="aafa8-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="aafa8-115">A `null` označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aafa8-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="aafa8-116">Prázdný řetězec ("") označuje platné heslo s nulovou délkou.</span><span class="sxs-lookup"><span data-stu-id="aafa8-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="aafa8-117">pro Ukazatel na platný `BSTR` , který označuje správné národní prostředí pro načtení informací.</span><span class="sxs-lookup"><span data-stu-id="aafa8-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="aafa8-118">V případě identifikátorů národního prostředí společnosti Microsoft je formát řetězce "MS\_*xxx*", kde *xxx* je řetězec v šestnáctkovém formátu, který označuje identifikátor národního prostředí (LCID).</span><span class="sxs-lookup"><span data-stu-id="aafa8-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="aafa8-119">Pokud je zadáno neplatné národní prostředí, vrátí `WBEM_E_INVALID_PARAMETER` se metoda s výjimkou systému Windows 7, kde je místo toho použito výchozí národní prostředí serveru.</span><span class="sxs-lookup"><span data-stu-id="aafa8-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="aafa8-120">Pokud je použito ' NULL1 ', aktuální národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="aafa8-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="aafa8-121">pro Příznaky, které mají být `ConnectServerWmi` předána metodě.</span><span class="sxs-lookup"><span data-stu-id="aafa8-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="aafa8-122">Hodnota nula (0) pro tento parametr způsobí, že volání `ConnectServerWmi` bude vráceno pouze po navázání připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="aafa8-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="aafa8-123">To může způsobit, že aplikace nereaguje na neomezenou dobu, pokud je server poškozený.</span><span class="sxs-lookup"><span data-stu-id="aafa8-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="aafa8-124">Další platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="aafa8-124">The other valid values are:</span></span>

| <span data-ttu-id="aafa8-125">Konstanta</span><span class="sxs-lookup"><span data-stu-id="aafa8-125">Constant</span></span>  | <span data-ttu-id="aafa8-126">Value</span><span class="sxs-lookup"><span data-stu-id="aafa8-126">Value</span></span>  | <span data-ttu-id="aafa8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="aafa8-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="aafa8-128">0x40</span><span class="sxs-lookup"><span data-stu-id="aafa8-128">0x40</span></span> | <span data-ttu-id="aafa8-129">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="aafa8-129">Reserved for internal use.</span></span> <span data-ttu-id="aafa8-130">Nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="aafa8-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="aafa8-131">0x80</span><span class="sxs-lookup"><span data-stu-id="aafa8-131">0x80</span></span> | <span data-ttu-id="aafa8-132">`ConnectServerWmi`Vrátí dvě minuty nebo méně.</span><span class="sxs-lookup"><span data-stu-id="aafa8-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="aafa8-133">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="aafa8-133">[in] The domain name of the user.</span></span> <span data-ttu-id="aafa8-134">Může mít následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="aafa8-134">It can have the following values:</span></span>

| <span data-ttu-id="aafa8-135">Value</span><span class="sxs-lookup"><span data-stu-id="aafa8-135">Value</span></span> | <span data-ttu-id="aafa8-136">Popis</span><span class="sxs-lookup"><span data-stu-id="aafa8-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="aafa8-137">trhnout</span><span class="sxs-lookup"><span data-stu-id="aafa8-137">blank</span></span> | <span data-ttu-id="aafa8-138">Používá se ověřování NTLM a doména NTLM aktuálního uživatele se používá.</span><span class="sxs-lookup"><span data-stu-id="aafa8-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="aafa8-139">Pokud `strUser` určuje doménu (doporučené umístění), nesmí se tady zadat.</span><span class="sxs-lookup"><span data-stu-id="aafa8-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="aafa8-140">Funkce se vrátí `WBEM_E_INVALID_PARAMETER` , pokud zadáte doménu v obou parametrech.</span><span class="sxs-lookup"><span data-stu-id="aafa8-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="aafa8-141">Kerberos:*hlavní název*</span><span class="sxs-lookup"><span data-stu-id="aafa8-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="aafa8-142">Použije se ověřování protokolem Kerberos a tento parametr obsahuje hlavní název protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="aafa8-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="aafa8-143">NTLMDOMAIN:*název domény*</span><span class="sxs-lookup"><span data-stu-id="aafa8-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="aafa8-144">Použije se ověřování NT LAN Manageru a tento parametr obsahuje název domény NTLM.</span><span class="sxs-lookup"><span data-stu-id="aafa8-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="aafa8-145">pro Obvykle je `null`tento parametr.</span><span class="sxs-lookup"><span data-stu-id="aafa8-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="aafa8-146">V opačném případě se jedná o ukazatel na objekt [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , který vyžaduje jeden nebo více zprostředkovatelů dynamické třídy.</span><span class="sxs-lookup"><span data-stu-id="aafa8-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="aafa8-147">mimo Když se funkce vrátí, přijme ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) vázaný na zadaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="aafa8-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="aafa8-148">Je nastavená tak, aby `null` odkazovala na chybu.</span><span class="sxs-lookup"><span data-stu-id="aafa8-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="aafa8-149">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="aafa8-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="aafa8-150">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="aafa8-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="aafa8-151">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aafa8-151">Return value</span></span>

<span data-ttu-id="aafa8-152">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="aafa8-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aafa8-153">Konstanta</span><span class="sxs-lookup"><span data-stu-id="aafa8-153">Constant</span></span>  |<span data-ttu-id="aafa8-154">Value</span><span class="sxs-lookup"><span data-stu-id="aafa8-154">Value</span></span>  |<span data-ttu-id="aafa8-155">Popis</span><span class="sxs-lookup"><span data-stu-id="aafa8-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="aafa8-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="aafa8-156">0x80041001</span></span> | <span data-ttu-id="aafa8-157">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="aafa8-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aafa8-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aafa8-158">0x80041008</span></span> | <span data-ttu-id="aafa8-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="aafa8-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aafa8-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aafa8-160">0x80041006</span></span> | <span data-ttu-id="aafa8-161">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="aafa8-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="aafa8-162">0</span><span class="sxs-lookup"><span data-stu-id="aafa8-162">0</span></span> | <span data-ttu-id="aafa8-163">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="aafa8-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="aafa8-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aafa8-164">Remarks</span></span>

<span data-ttu-id="aafa8-165">Tato funkce zalomí volání metody [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .</span><span class="sxs-lookup"><span data-stu-id="aafa8-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="aafa8-166">Pro místní přístup k výchozímu oboru názvů `strNetworkResource` může být cesta jednoduchého objektu: "root\default" nebo "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="aafa8-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="aafa8-167">Pro přístup k výchozímu oboru názvů na vzdáleném počítači pomocí modelu COM nebo sítě kompatibilního se společností Microsoft zadejte název počítače\\: "myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="aafa8-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="aafa8-168">Název počítače může být taky název DNS nebo IP adresa.</span><span class="sxs-lookup"><span data-stu-id="aafa8-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="aafa8-169">`ConnectServerWmi` Funkce se také může připojit k počítačům s protokolem IPv6 pomocí adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="aafa8-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="aafa8-170">`strUser`nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="aafa8-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="aafa8-171">Pokud je doména určena v `strAuthority`, nesmí být také obsažena v `strUser`nebo funkce vrácena `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="aafa8-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="aafa8-172">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aafa8-172">Requirements</span></span>

 <span data-ttu-id="aafa8-173">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aafa8-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="aafa8-174">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="aafa8-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="aafa8-175">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aafa8-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aafa8-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aafa8-176">See also</span></span>

- [<span data-ttu-id="aafa8-177">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="aafa8-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
