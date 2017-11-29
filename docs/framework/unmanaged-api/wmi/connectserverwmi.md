---
title: "Funkce ConnectServerWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce ConnectServerWmi DCOM používá k vytvoření připojení k oboru názvů WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ConnectServerWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ConnectServerWmi
helpviewer_keywords: ConnectServerWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b51050bce4603ebcfe99fb38d66e54683c677293
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="40555-103">ConnectServerWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="40555-103">ConnectServerWmi function</span></span>
<span data-ttu-id="40555-104">Vytvoří připojení přes DCOM k oboru názvů WMI v zadaném počítači.</span><span class="sxs-lookup"><span data-stu-id="40555-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="40555-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40555-105">Syntax</span></span>  
  
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
## <a name="parameters"></a><span data-ttu-id="40555-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40555-106">Parameters</span></span>

<span data-ttu-id="40555-107">`strNetworkResource`[v] Ukazatel na platnou `BSTR` obsahující cestu objektu správný obor názvů rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="40555-107">`strNetworkResource` [in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="40555-108">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="40555-108">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="40555-109">`strUser`[v] Ukazatel na platnou `BSTR` obsahující uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="40555-109">`strUser` [in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="40555-110">A `null` hodnota označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40555-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="40555-111">Pokud je uživatel z jiné domény než aktuální, `strUser` může také obsahovat doména a uživatelské jméno, které jsou oddělené zpětným lomítkem.</span><span class="sxs-lookup"><span data-stu-id="40555-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="40555-112">`strUser`Můžete také být v uživatele hlavní název (UPN) formátovat, suhc jako  *userName@domainName* .</span><span class="sxs-lookup"><span data-stu-id="40555-112">`strUser` can also be in user principal name (UPN) format, suhc as *userName@domainName*.</span></span> <span data-ttu-id="40555-113">Najdete v článku [poznámky](#remarks) části Další informace.</span><span class="sxs-lookup"><span data-stu-id="40555-113">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="40555-114">`strPassword`[v] Ukazatel na platnou `BSTR` obsahující heslo.</span><span class="sxs-lookup"><span data-stu-id="40555-114">`strPassword` [in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="40555-115">A `null` označuje aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40555-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="40555-116">Prázdný řetězec ("") označuje platné heslo nulové délky.</span><span class="sxs-lookup"><span data-stu-id="40555-116">An empty string ("") indicates a valid zero-length password.</span></span>

<span data-ttu-id="40555-117">`strLocale`[v] Ukazatel na platnou `BSTR` určující správné národní prostředí pro načítání informací.</span><span class="sxs-lookup"><span data-stu-id="40555-117">`strLocale` [in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="40555-118">Identifikátory národního prostředí Microsoft je formát řetězce "MS\_*xxx*", kde *xxx* je řetězce v šestnáctkovém formátu, který označuje identifikátor národního prostředí (LCID).</span><span class="sxs-lookup"><span data-stu-id="40555-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="40555-119">Pokud je zadán neplatný národního prostředí, vrátí metoda `WBEM_E_INVALID_PARAMETER` s výjimkou ve Windows 7, kde bude místo něj použita výchozí národní prostředí serveru.</span><span class="sxs-lookup"><span data-stu-id="40555-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="40555-120">Pokud se používá null1, aktuální národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="40555-120">If \`null1, the current locale is used.</span></span> 
 
<span data-ttu-id="40555-121">`lSecurityFlags`[v] Příznaky, které mají být předány `ConnectServerWmi` metoda.</span><span class="sxs-lookup"><span data-stu-id="40555-121">`lSecurityFlags` [in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="40555-122">Hodnota nula (0) pro tento parametr je výsledkem volání `ConnectServerWmi` vrací pouze po vytvoření připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="40555-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="40555-123">Výsledkem může být aplikace neodpovídá po neomezenou dobu Pokud server se přeruší.</span><span class="sxs-lookup"><span data-stu-id="40555-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="40555-124">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="40555-124">The other valid values are:</span></span>

| <span data-ttu-id="40555-125">Konstanta</span><span class="sxs-lookup"><span data-stu-id="40555-125">Constant</span></span>  | <span data-ttu-id="40555-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40555-126">Value</span></span>  | <span data-ttu-id="40555-127">Popis</span><span class="sxs-lookup"><span data-stu-id="40555-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="40555-128">0x40</span><span class="sxs-lookup"><span data-stu-id="40555-128">0x40</span></span> | <span data-ttu-id="40555-129">Vyhrazeno pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="40555-129">Reserved for internal use.</span></span> <span data-ttu-id="40555-130">Nepoužívejte.</span><span class="sxs-lookup"><span data-stu-id="40555-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="40555-131">0x80</span><span class="sxs-lookup"><span data-stu-id="40555-131">0x80</span></span> | <span data-ttu-id="40555-132">`ConnectServerWmi`Vrátí za dvě minuty nebo méně.</span><span class="sxs-lookup"><span data-stu-id="40555-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

<span data-ttu-id="40555-133">`strAuthority`[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="40555-133">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="40555-134">Může mít následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="40555-134">It can have the following values:</span></span>

| <span data-ttu-id="40555-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40555-135">Value</span></span> | <span data-ttu-id="40555-136">Popis</span><span class="sxs-lookup"><span data-stu-id="40555-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="40555-137">Prázdné</span><span class="sxs-lookup"><span data-stu-id="40555-137">blank</span></span> | <span data-ttu-id="40555-138">Použít ověřování NTLM a NTLM domény aktuálního uživatele se používá.</span><span class="sxs-lookup"><span data-stu-id="40555-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="40555-139">Pokud `strUser` Určuje doménu (doporučené umístění), nesmí být zadaný v tomto poli.</span><span class="sxs-lookup"><span data-stu-id="40555-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="40555-140">Funkce vrátí hodnotu `WBEM_E_INVALID_PARAMETER` Pokud v oba parametry zadejte doménu.</span><span class="sxs-lookup"><span data-stu-id="40555-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="40555-141">Pomocí protokolu Kerberos:*hlavní název*</span><span class="sxs-lookup"><span data-stu-id="40555-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="40555-142">Používáno ověřování protokolem Kerberos a tento parametr obsahuje hlavní název protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="40555-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="40555-143">NTLMDOMAIN:*název domény*</span><span class="sxs-lookup"><span data-stu-id="40555-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="40555-144">Se používá ověřování NT LAN Manager a tento parametr obsahuje název domény protokolu NTLM.</span><span class="sxs-lookup"><span data-stu-id="40555-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`   
<span data-ttu-id="40555-145">[v] Obvykle je tento parametr je `null`.</span><span class="sxs-lookup"><span data-stu-id="40555-145">[in] Typically, this parameter is is `null`.</span></span> <span data-ttu-id="40555-146">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) vyžaduje jeden nebo více poskytovatelů dynamické třídy objektu.</span><span class="sxs-lookup"><span data-stu-id="40555-146">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) object required by one or more dynamic class providers.</span></span> 

`ppNamespace`  
<span data-ttu-id="40555-147">[out] V případě, že funkce vrátí hodnotu, obdrží ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) vázaný objekt pro zadaný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="40555-147">[out] When the function returns, receives a pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object bound to the specified namespace.</span></span> <span data-ttu-id="40555-148">Je nastaven tak, aby odkazoval `null` když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="40555-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`  
<span data-ttu-id="40555-149">[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="40555-149">[in] The impersonation level.</span></span>

`authLevel`  
<span data-ttu-id="40555-150">[v] Úroveň ověřování.</span><span class="sxs-lookup"><span data-stu-id="40555-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="40555-151">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40555-151">Return value</span></span>

<span data-ttu-id="40555-152">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="40555-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="40555-153">Konstanta</span><span class="sxs-lookup"><span data-stu-id="40555-153">Constant</span></span>  |<span data-ttu-id="40555-154">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40555-154">Value</span></span>  |<span data-ttu-id="40555-155">Popis</span><span class="sxs-lookup"><span data-stu-id="40555-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="40555-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="40555-156">0x80041001</span></span> | <span data-ttu-id="40555-157">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="40555-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="40555-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="40555-158">0x80041008</span></span> | <span data-ttu-id="40555-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="40555-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="40555-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="40555-160">0x80041006</span></span> | <span data-ttu-id="40555-161">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="40555-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="40555-162">0</span><span class="sxs-lookup"><span data-stu-id="40555-162">0</span></span> | <span data-ttu-id="40555-163">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="40555-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="40555-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40555-164">Remarks</span></span>

<span data-ttu-id="40555-165">Tato funkce zabalí volání [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="40555-165">This function wraps a call to the [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) method.</span></span>

 <span data-ttu-id="40555-166">Pro místní přístup k výchozí obor názvů `strNetworkResource` může být cesta jednoduchého objektu: "root\default" nebo "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="40555-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="40555-167">Pro přístup k výchozí obor názvů na vzdáleném počítači pomocí modelu COM nebo kompatibilní se službou Microsoft sítě, zahrnují název počítače: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="40555-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="40555-168">Název počítače může také být, název DNS nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="40555-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="40555-169">`ConnectServerWmi` Funkce se může připojit i s počítači se systémem IPv6 pomocí adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="40555-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="40555-170">`strUser`nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="40555-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="40555-171">Jestliže se v doméně `strAuthority`, se nesmí být zahrnuto do `strUser`, nebo funkce vrátí hodnotu `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="40555-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>


## <a name="requirements"></a><span data-ttu-id="40555-172">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40555-172">Requirements</span></span>  
 <span data-ttu-id="40555-173">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40555-173">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40555-174">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="40555-174">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="40555-175">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="40555-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40555-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="40555-176">See also</span></span>  
[<span data-ttu-id="40555-177">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="40555-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
