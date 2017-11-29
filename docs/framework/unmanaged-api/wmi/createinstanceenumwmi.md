---
title: "Funkce CreateInstanceEnumWmi (referenční dokumentace nespravovaného rozhraní API)"
description: "Funkce CreateInstanceEnumWmi vrací enumerátor obsahující instance dané třídy, které splňují kritéria pro výběr."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19a4102796da7a5692eb5b9b459a6a95ff7409f9
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="029e0-103">CreateInstanceEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="029e0-103">CreateInstanceEnumWmi function</span></span>
<span data-ttu-id="029e0-104">Vrátí enumerátor, který vrátí instance dané třídy, které splňují kritéria zadaná výběru.</span><span class="sxs-lookup"><span data-stu-id="029e0-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="029e0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="029e0-105">Syntax</span></span>  
  
```  
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

## <a name="parameters"></a><span data-ttu-id="029e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="029e0-106">Parameters</span></span>

`strFilter`    
<span data-ttu-id="029e0-107">[v] Název třídy, pro kterou instancí potřeby.</span><span class="sxs-lookup"><span data-stu-id="029e0-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="029e0-108">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="029e0-108">This parameter cannot be `null`.</span></span>

`lFlags`   
<span data-ttu-id="029e0-109">[v] Kombinace příznaky, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="029e0-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="029e0-110">Následující hodnoty jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="029e0-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="029e0-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="029e0-111">Constant</span></span>  |<span data-ttu-id="029e0-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="029e0-112">Value</span></span>  |<span data-ttu-id="029e0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="029e0-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="029e0-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="029e0-114">0x20000</span></span> | <span data-ttu-id="029e0-115">Pokud sadu, funkce načte doplněné kvalifikátory uložené v lokalizovaných obor názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="029e0-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="029e0-116">Pokud není sada, funkce načte pouze kvalifikátory uložené v oboru názvů okamžitou.</span><span class="sxs-lookup"><span data-stu-id="029e0-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="029e0-117">0</span><span class="sxs-lookup"><span data-stu-id="029e0-117">0</span></span> | <span data-ttu-id="029e0-118">Výčet obsahuje tento a všechny podtřídy v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="029e0-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="029e0-119">1</span><span class="sxs-lookup"><span data-stu-id="029e0-119">1</span></span> | <span data-ttu-id="029e0-120">Výčet obsahuje pouze čistý instance této třídy a vyloučí všechny instance podtříd zadat vlastnosti nebyl nalezen v této třídě.</span><span class="sxs-lookup"><span data-stu-id="029e0-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="029e0-121">0x10</span><span class="sxs-lookup"><span data-stu-id="029e0-121">0x10</span></span> | <span data-ttu-id="029e0-122">Příznak způsobí, že polosynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="029e0-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="029e0-123">0x20</span><span class="sxs-lookup"><span data-stu-id="029e0-123">0x20</span></span> | <span data-ttu-id="029e0-124">Vrátí enumerátor dopředné.</span><span class="sxs-lookup"><span data-stu-id="029e0-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="029e0-125">Obvykle dopředných enumerátory je rychlejší a využívají méně paměti než konvenční výčty, ale nepovoluje volání [klon](clone.md).</span><span class="sxs-lookup"><span data-stu-id="029e0-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="029e0-126">0</span><span class="sxs-lookup"><span data-stu-id="029e0-126">0</span></span> | <span data-ttu-id="029e0-127">Rozhraní WMI zachová ukazatelé na objekty v enumration, dokud jejich vydání.</span><span class="sxs-lookup"><span data-stu-id="029e0-127">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="029e0-128">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="029e0-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="029e0-129">[v] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="029e0-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="029e0-130">Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instanci, která může být používán zprostředkovatele, který poskytuje požadovaný instancí.</span><span class="sxs-lookup"><span data-stu-id="029e0-130">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`  
<span data-ttu-id="029e0-131">[out] Obdrží má ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="029e0-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="029e0-132">[v] Úroveň ověřování.</span><span class="sxs-lookup"><span data-stu-id="029e0-132">[in] The authorization level.</span></span>

<span data-ttu-id="029e0-133">`impLevel`[v] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="029e0-133">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="029e0-134">[v] Ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="029e0-134">[in] A pointer to an [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="029e0-135">[v] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="029e0-135">[in] The user name.</span></span> <span data-ttu-id="029e0-136">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="029e0-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="029e0-137">[v] Heslo.</span><span class="sxs-lookup"><span data-stu-id="029e0-137">[in] The password.</span></span> <span data-ttu-id="029e0-138">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="029e0-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="029e0-139">[v] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="029e0-139">[in] The domain name of the user.</span></span> <span data-ttu-id="029e0-140">Najdete v článku [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="029e0-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="029e0-141">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="029e0-141">Return value</span></span>

<span data-ttu-id="029e0-142">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="029e0-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="029e0-143">Konstanta</span><span class="sxs-lookup"><span data-stu-id="029e0-143">Constant</span></span>  |<span data-ttu-id="029e0-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="029e0-144">Value</span></span>  |<span data-ttu-id="029e0-145">Popis</span><span class="sxs-lookup"><span data-stu-id="029e0-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="029e0-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="029e0-146">0x80041003</span></span> | <span data-ttu-id="029e0-147">Uživatel nemá oprávnění k zobrazení instance pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="029e0-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="029e0-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="029e0-148">0x80041001</span></span> | <span data-ttu-id="029e0-149">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="029e0-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="029e0-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="029e0-150">0x80041010</span></span> | <span data-ttu-id="029e0-151">`strFilter`neexistuje.</span><span class="sxs-lookup"><span data-stu-id="029e0-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="029e0-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="029e0-152">0x80041008</span></span> | <span data-ttu-id="029e0-153">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="029e0-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="029e0-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="029e0-154">0x80041006</span></span> | <span data-ttu-id="029e0-155">Je k dispozici k dokončení operace není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="029e0-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="029e0-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="029e0-156">0x80041033</span></span> | <span data-ttu-id="029e0-157">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="029e0-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="029e0-158">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="029e0-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="029e0-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="029e0-159">0x80041015</span></span> | <span data-ttu-id="029e0-160">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraní WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="029e0-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="029e0-161">0</span><span class="sxs-lookup"><span data-stu-id="029e0-161">0</span></span> | <span data-ttu-id="029e0-162">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="029e0-162">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="029e0-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="029e0-163">Remarks</span></span>

<span data-ttu-id="029e0-164">Tato funkce zabalí volání [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="029e0-164">This function wraps a call to the [IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="029e0-165">Všimněte si, že vrácený enumerátor může mít nulovým počtem elementů.</span><span class="sxs-lookup"><span data-stu-id="029e0-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="029e0-166">Pokud volání funkce selže, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="029e0-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="029e0-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="029e0-167">Requirements</span></span>  
 <span data-ttu-id="029e0-168">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="029e0-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="029e0-169">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="029e0-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="029e0-170">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="029e0-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029e0-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="029e0-171">See also</span></span>  
[<span data-ttu-id="029e0-172">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="029e0-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
