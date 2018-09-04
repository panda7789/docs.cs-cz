---
title: Funkce ConnectServerWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ConnectServerWmi používá model DCOM k vytvoření připojení k oboru názvů WMI.
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
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540880"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="5d355-103">ConnectServerWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="5d355-103">ConnectServerWmi function</span></span>
<span data-ttu-id="5d355-104">Připojení přes DCOM k oboru názvů WMI vytvoří v zadaném počítači.</span><span class="sxs-lookup"><span data-stu-id="5d355-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5d355-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d355-105">Syntax</span></span>  
  
```  
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
## <a name="parameters"></a><span data-ttu-id="5d355-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d355-106">Parameters</span></span>

<span data-ttu-id="5d355-107">`strNetworkResource` [in] Ukazatel na platný `BSTR` , který obsahuje cestu k objektu správný obor názvů rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="5d355-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="5d355-108">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="5d355-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="5d355-109">`strUser` [in] Ukazatel na platný `BSTR` , která obsahuje uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="5d355-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="5d355-110">A `null` hodnota označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5d355-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="5d355-111">Pokud se uživatel nachází v jiné doméně než tu, `strUser` může také obsahovat doména a uživatelské jméno oddělené zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="5d355-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="5d355-112">`strUser` Můžete také být v uživatelském hlavní název (UPN) naformátovat, suhc jako *userName@domainName*.</span><span class="sxs-lookup"><span data-stu-id="5d355-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="5d355-113">Zobrazit [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="5d355-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="5d355-114">`strPassword` [in] Ukazatel na platný `BSTR` obsahující heslo.</span><span class="sxs-lookup"><span data-stu-id="5d355-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="5d355-115">A `null` označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5d355-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="5d355-116">Prázdný řetězec ("") označuje platné heslo nulové délky.</span><span class="sxs-lookup"><span data-stu-id="5d355-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="5d355-117">`strLocale` [in] Ukazatel na platný `BSTR` určující správné národní prostředí pro načítání informací.</span><span class="sxs-lookup"><span data-stu-id="5d355-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="5d355-118">Identifikátory národního prostředí Microsoft formát řetězce je "MS\_*xxx*", kde *xxx* je řetězce v šestnáctkovém formátu, který určuje identifikátor národního prostředí (LCID).</span><span class="sxs-lookup"><span data-stu-id="5d355-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="5d355-119">Pokud je zadán neplatný národní prostředí, vrátí metoda `WBEM_E_INVALID_PARAMETER` s výjimkou Windows 7, které místo toho používají výchozí národní prostředí serveru.</span><span class="sxs-lookup"><span data-stu-id="5d355-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="5d355-120">Pokud se používá null1 aktuálního národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="5d355-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="5d355-121">`lSecurityFlags` [in] Příznaky, které mají být předány `ConnectServerWmi` metody.</span><span class="sxs-lookup"><span data-stu-id="5d355-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="5d355-122">Hodnotu nula (0) pro tento parametr je výsledkem volání `ConnectServerWmi` vrací pouze po navázání připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="5d355-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="5d355-123">To může způsobit aplikace neodpovídá po neomezenou dobu Pokud na serveru se přeruší.</span><span class="sxs-lookup"><span data-stu-id="5d355-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="5d355-124">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5d355-124">The other valid values are:</span></span>

| <span data-ttu-id="5d355-125">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d355-125">Constant</span></span>  | <span data-ttu-id="5d355-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5d355-126">Value</span></span>  | <span data-ttu-id="5d355-127">Popis</span><span class="sxs-lookup"><span data-stu-id="5d355-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="5d355-128">0x40</span><span class="sxs-lookup"><span data-stu-id="5d355-128">0x40</span></span> | <span data-ttu-id="5d355-129">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="5d355-129">Reserved for internal use.</span></span> <span data-ttu-id="5d355-130">Nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="5d355-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="5d355-131">0x80</span><span class="sxs-lookup"><span data-stu-id="5d355-131">0x80</span></span> | <span data-ttu-id="5d355-132">`ConnectServerWmi` vrátí do dvou minut nebo i rychleji.</span><span class="sxs-lookup"><span data-stu-id="5d355-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="5d355-133">`strAuthority` [in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="5d355-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="5d355-134">Může mít následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="5d355-134">It can have the following values:</span></span>

| <span data-ttu-id="5d355-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5d355-135">Value</span></span> | <span data-ttu-id="5d355-136">Popis</span><span class="sxs-lookup"><span data-stu-id="5d355-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="5d355-137">Prázdné</span><span class="sxs-lookup"><span data-stu-id="5d355-137">blank</span></span> | <span data-ttu-id="5d355-138">Bude použito ověřování NTLM a používá NTLM domény aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="5d355-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="5d355-139">Pokud `strUser` Určuje doménu (doporučené umístění), nesmí být zadané tady.</span><span class="sxs-lookup"><span data-stu-id="5d355-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="5d355-140">Funkce vrátí `WBEM_E_INVALID_PARAMETER` při zadání domény v obou parametrech.</span><span class="sxs-lookup"><span data-stu-id="5d355-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="5d355-141">Pomocí protokolu Kerberos:*hlavní název*</span><span class="sxs-lookup"><span data-stu-id="5d355-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="5d355-142">Používáno ověřování protokolem Kerberos a tento parametr obsahuje hlavní název Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5d355-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="5d355-143">NTLMDOMAIN:*název domény*</span><span class="sxs-lookup"><span data-stu-id="5d355-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="5d355-144">Ověřování NT LAN Manager se používá, a tento parametr obsahuje název domény NTLM.</span><span class="sxs-lookup"><span data-stu-id="5d355-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="5d355-145">[in] Obvykle je tento parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="5d355-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="5d355-146">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) podle jednoho nebo více dynamických tříd zprostředkovatelů je požadován objekt.</span><span class="sxs-lookup"><span data-stu-id="5d355-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="5d355-147">[out] Po návratu funkce přijímá ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt vázán na určený obor názvů.</span><span class="sxs-lookup"><span data-stu-id="5d355-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="5d355-148">Je nastaven tak, aby odkazoval na `null` když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5d355-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="5d355-149">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="5d355-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="5d355-150">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="5d355-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d355-151">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d355-151">Return value</span></span>

<span data-ttu-id="5d355-152">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="5d355-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5d355-153">Konstanta</span><span class="sxs-lookup"><span data-stu-id="5d355-153">Constant</span></span>  |<span data-ttu-id="5d355-154">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5d355-154">Value</span></span>  |<span data-ttu-id="5d355-155">Popis</span><span class="sxs-lookup"><span data-stu-id="5d355-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5d355-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5d355-156">0x80041001</span></span> | <span data-ttu-id="5d355-157">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="5d355-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5d355-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5d355-158">0x80041008</span></span> | <span data-ttu-id="5d355-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="5d355-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5d355-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5d355-160">0x80041006</span></span> | <span data-ttu-id="5d355-161">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="5d355-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5d355-162">0</span><span class="sxs-lookup"><span data-stu-id="5d355-162">0</span></span> | <span data-ttu-id="5d355-163">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5d355-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5d355-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d355-164">Remarks</span></span>

<span data-ttu-id="5d355-165">Tato funkce zalamuje volání na [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metody.</span><span class="sxs-lookup"><span data-stu-id="5d355-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="5d355-166">Pro místní přístup k výchozí obor názvů `strNetworkResource` může být jednoduchý objekt cesta: "root\default" nebo "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="5d355-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="5d355-167">Pro přístup k výchozí obor názvů ve vzdáleném počítači pomocí modelu COM nebo Microsoft kompatibilní sítě, zahrnují název počítače: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="5d355-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="5d355-168">Název počítače může také být, název DNS nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="5d355-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="5d355-169">`ConnectServerWmi` Funkce se také připojit pomocí počítače se systémem IPv6 pomocí adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="5d355-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="5d355-170">`strUser` Nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5d355-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="5d355-171">Pokud je v zadané doméně `strAuthority`, se nesmí být i součástí `strUser`, nebo funkce vrátí `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="5d355-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="5d355-172">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d355-172">Requirements</span></span>  
 <span data-ttu-id="5d355-173">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d355-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d355-174">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5d355-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5d355-175">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5d355-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d355-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d355-176">See also</span></span>  
[<span data-ttu-id="5d355-177">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="5d355-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
