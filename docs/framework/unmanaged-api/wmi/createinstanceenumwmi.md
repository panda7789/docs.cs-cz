---
title: Funkce CreateInstanceEnumWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CreateInstanceEnumWmi vrací enumerátor obsahující instance dané třídy, které splňují kritéria pro výběr.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a1d082cae19bd83c90e063d841a0c9e4602bc40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040700"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="9ebce-103">CreateInstanceEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="9ebce-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="9ebce-104">Vrátí enumerátor, který vrátí instance dané třídy, které splňují kritéria zadaná výběru.</span><span class="sxs-lookup"><span data-stu-id="9ebce-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9ebce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ebce-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
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

## <a name="parameters"></a><span data-ttu-id="9ebce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ebce-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="9ebce-107">[in] Název třídy, pro které jsou požadované instancí.</span><span class="sxs-lookup"><span data-stu-id="9ebce-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="9ebce-108">Tento parametr nemůže mít `null`.</span><span class="sxs-lookup"><span data-stu-id="9ebce-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="9ebce-109">[in] Kombinace příznaků, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="9ebce-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9ebce-110">Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9ebce-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9ebce-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9ebce-111">Constant</span></span>  |<span data-ttu-id="9ebce-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9ebce-112">Value</span></span>  |<span data-ttu-id="9ebce-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9ebce-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9ebce-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="9ebce-114">0x20000</span></span> | <span data-ttu-id="9ebce-115">Pokud sada funkce načte upravenou kvalifikátory uložené v lokalizovaných názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="9ebce-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="9ebce-116">Pokud není sada, funkce načte jenom v kvalifikátorech uložené v oboru názvů okamžité.</span><span class="sxs-lookup"><span data-stu-id="9ebce-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="9ebce-117">0</span><span class="sxs-lookup"><span data-stu-id="9ebce-117">0</span></span> | <span data-ttu-id="9ebce-118">Výčet zahrnuje tento a všechny podtřídy v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="9ebce-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="9ebce-119">1</span><span class="sxs-lookup"><span data-stu-id="9ebce-119">1</span></span> | <span data-ttu-id="9ebce-120">Výčet obsahuje pouze čistě instance této třídy a vyloučí všechny výskyty podtříd zadat vlastnosti nebyla nalezena v této třídě.</span><span class="sxs-lookup"><span data-stu-id="9ebce-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9ebce-121">0x10</span><span class="sxs-lookup"><span data-stu-id="9ebce-121">0x10</span></span> | <span data-ttu-id="9ebce-122">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="9ebce-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="9ebce-123">0x20</span><span class="sxs-lookup"><span data-stu-id="9ebce-123">0x20</span></span> | <span data-ttu-id="9ebce-124">Vrátí enumerátor pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="9ebce-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="9ebce-125">Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="9ebce-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="9ebce-126">0</span><span class="sxs-lookup"><span data-stu-id="9ebce-126">0</span></span> | <span data-ttu-id="9ebce-127">Rozhraní WMI uchovává ukazatelů na objekty ve výčtu, dokud se neuvolní.</span><span class="sxs-lookup"><span data-stu-id="9ebce-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="9ebce-128">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro zajištění nejlepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="9ebce-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="9ebce-129">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="9ebce-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9ebce-130">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež mohou využívat poskytovatele, který poskytuje požadovaná instance.</span><span class="sxs-lookup"><span data-stu-id="9ebce-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="9ebce-131">[out] Přijímá ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9ebce-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="9ebce-132">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="9ebce-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="9ebce-133">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="9ebce-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="9ebce-134">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="9ebce-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="9ebce-135">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="9ebce-135">[in] The user name.</span></span> <span data-ttu-id="9ebce-136">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9ebce-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="9ebce-137">[in] Heslo.</span><span class="sxs-lookup"><span data-stu-id="9ebce-137">[in] The password.</span></span> <span data-ttu-id="9ebce-138">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9ebce-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="9ebce-139">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="9ebce-139">[in] The domain name of the user.</span></span> <span data-ttu-id="9ebce-140">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9ebce-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ebce-141">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ebce-141">Return value</span></span>

<span data-ttu-id="9ebce-142">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9ebce-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9ebce-143">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9ebce-143">Constant</span></span>  |<span data-ttu-id="9ebce-144">Value</span><span class="sxs-lookup"><span data-stu-id="9ebce-144">Value</span></span>  |<span data-ttu-id="9ebce-145">Popis</span><span class="sxs-lookup"><span data-stu-id="9ebce-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9ebce-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9ebce-146">0x80041003</span></span> | <span data-ttu-id="9ebce-147">Uživatel nemá oprávnění k zobrazení instance dané třídy.</span><span class="sxs-lookup"><span data-stu-id="9ebce-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9ebce-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9ebce-148">0x80041001</span></span> | <span data-ttu-id="9ebce-149">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="9ebce-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9ebce-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9ebce-150">0x80041010</span></span> | <span data-ttu-id="9ebce-151">`strFilter` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9ebce-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9ebce-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9ebce-152">0x80041008</span></span> | <span data-ttu-id="9ebce-153">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="9ebce-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9ebce-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9ebce-154">0x80041006</span></span> | <span data-ttu-id="9ebce-155">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="9ebce-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9ebce-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9ebce-156">0x80041033</span></span> | <span data-ttu-id="9ebce-157">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="9ebce-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9ebce-158">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="9ebce-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9ebce-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9ebce-159">0x80041015</span></span> | <span data-ttu-id="9ebce-160">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="9ebce-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9ebce-161">0</span><span class="sxs-lookup"><span data-stu-id="9ebce-161">0</span></span> | <span data-ttu-id="9ebce-162">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9ebce-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="9ebce-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ebce-163">Remarks</span></span>

<span data-ttu-id="9ebce-164">Tato funkce zalamuje volání na [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) metody.</span><span class="sxs-lookup"><span data-stu-id="9ebce-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="9ebce-165">Všimněte si, že vrácené enumerátor může mít nulovým počtem elementů.</span><span class="sxs-lookup"><span data-stu-id="9ebce-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="9ebce-166">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9ebce-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ebce-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ebce-167">Requirements</span></span>

<span data-ttu-id="9ebce-168">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ebce-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9ebce-169">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9ebce-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="9ebce-170">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ebce-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9ebce-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ebce-171">See also</span></span>

- [<span data-ttu-id="9ebce-172">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9ebce-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)