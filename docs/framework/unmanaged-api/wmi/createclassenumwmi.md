---
title: Funkce CreateClassEnumWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CreateClassEnumWmi vrátí enumerátor pro všechny třídy, které splňují zadaná kritéria.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3777319f818b7652157147f458b81d9935805b1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636992"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="9b864-103">CreateClassEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="9b864-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="9b864-104">Vrátí enumerátor pro všechny třídy, které splňují kritéria zadaná výběru.</span><span class="sxs-lookup"><span data-stu-id="9b864-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9b864-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b864-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="9b864-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b864-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="9b864-107">[in] Pokud není `null` nebo prázdnou, určí název nadřazené třídu; vrátí enumerátor pouze podtřídy této třídy.</span><span class="sxs-lookup"><span data-stu-id="9b864-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="9b864-108">Pokud je `null` nebo prázdné a `lFlags` WBEM_FLAG_SHALLOW se vrátí jenom nejvyšší úrovně třídy (třídy s žádnou nadřazené třídu).</span><span class="sxs-lookup"><span data-stu-id="9b864-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="9b864-109">Pokud je `null` nebo prázdné a `lFlags` je `WBEM_FLAG_DEEP`, vrátí všechny třídy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9b864-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="9b864-110">[in] Kombinace příznaků, které ovlivňují chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="9b864-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="9b864-111">Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9b864-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9b864-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9b864-112">Constant</span></span>  |<span data-ttu-id="9b864-113">Value</span><span class="sxs-lookup"><span data-stu-id="9b864-113">Value</span></span>  |<span data-ttu-id="9b864-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9b864-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="9b864-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="9b864-115">0x20000</span></span> | <span data-ttu-id="9b864-116">Pokud sada funkce načte upravenou kvalifikátory uložené v lokalizovaných názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="9b864-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="9b864-117">Pokud není sada, funkce načte jenom v kvalifikátorech uložené v oboru názvů okamžité.</span><span class="sxs-lookup"><span data-stu-id="9b864-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="9b864-118">0</span><span class="sxs-lookup"><span data-stu-id="9b864-118">0</span></span> | <span data-ttu-id="9b864-119">Výčet zahrnuje všechny podtřídy v hierarchii, ale ne této třídy.</span><span class="sxs-lookup"><span data-stu-id="9b864-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="9b864-120">1</span><span class="sxs-lookup"><span data-stu-id="9b864-120">1</span></span> | <span data-ttu-id="9b864-121">Výčet obsahuje pouze čistě instance této třídy a vyloučí všechny výskyty podtříd zadat vlastnosti nebyla nalezena v této třídě.</span><span class="sxs-lookup"><span data-stu-id="9b864-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="9b864-122">0x10</span><span class="sxs-lookup"><span data-stu-id="9b864-122">0x10</span></span> | <span data-ttu-id="9b864-123">Příznak způsobí, že volání semisynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="9b864-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="9b864-124">0x20</span><span class="sxs-lookup"><span data-stu-id="9b864-124">0x20</span></span> | <span data-ttu-id="9b864-125">Vrátí enumerátor pouze vpřed.</span><span class="sxs-lookup"><span data-stu-id="9b864-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="9b864-126">Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="9b864-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="9b864-127">0</span><span class="sxs-lookup"><span data-stu-id="9b864-127">0</span></span> | <span data-ttu-id="9b864-128">Rozhraní WMI uchovává ukazatelů na objekty ve výčtu, dokud se neuvolní.</span><span class="sxs-lookup"><span data-stu-id="9b864-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="9b864-129">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro zajištění nejlepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="9b864-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="9b864-130">[in] Obvykle je tato hodnota `null`.</span><span class="sxs-lookup"><span data-stu-id="9b864-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="9b864-131">V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="9b864-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="9b864-132">[out] Přijímá ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9b864-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="9b864-133">[in] Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="9b864-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="9b864-134">[in] Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="9b864-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="9b864-135">[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt, který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="9b864-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="9b864-136">[in] Uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="9b864-136">[in] The user name.</span></span> <span data-ttu-id="9b864-137">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9b864-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="9b864-138">[in] Heslo.</span><span class="sxs-lookup"><span data-stu-id="9b864-138">[in] The password.</span></span> <span data-ttu-id="9b864-139">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9b864-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="9b864-140">[in] Název domény uživatele.</span><span class="sxs-lookup"><span data-stu-id="9b864-140">[in] The domain name of the user.</span></span> <span data-ttu-id="9b864-141">Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.</span><span class="sxs-lookup"><span data-stu-id="9b864-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="9b864-142">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b864-142">Return value</span></span>

<span data-ttu-id="9b864-143">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9b864-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9b864-144">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9b864-144">Constant</span></span>  |<span data-ttu-id="9b864-145">Value</span><span class="sxs-lookup"><span data-stu-id="9b864-145">Value</span></span>  |<span data-ttu-id="9b864-146">Popis</span><span class="sxs-lookup"><span data-stu-id="9b864-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="9b864-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="9b864-147">0x80041003</span></span> | <span data-ttu-id="9b864-148">Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které funkce může vrátit.</span><span class="sxs-lookup"><span data-stu-id="9b864-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="9b864-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9b864-149">0x80041001</span></span> | <span data-ttu-id="9b864-150">Došlo k nespecifikované chybě.</span><span class="sxs-lookup"><span data-stu-id="9b864-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="9b864-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="9b864-151">0x80041010</span></span> | <span data-ttu-id="9b864-152">`strSuperClass` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9b864-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9b864-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9b864-153">0x80041008</span></span> | <span data-ttu-id="9b864-154">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="9b864-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9b864-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9b864-155">0x80041006</span></span> | <span data-ttu-id="9b864-156">Nedostatek paměti je k dispozici k dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="9b864-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="9b864-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="9b864-157">0x80041033</span></span> | <span data-ttu-id="9b864-158">Služba WMI byla pravděpodobně zastavena a restartování.</span><span class="sxs-lookup"><span data-stu-id="9b864-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="9b864-159">Volání [ConnectServerWmi](connectserverwmi.md) znovu.</span><span class="sxs-lookup"><span data-stu-id="9b864-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="9b864-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="9b864-160">0x80041015</span></span> | <span data-ttu-id="9b864-161">Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil.</span><span class="sxs-lookup"><span data-stu-id="9b864-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9b864-162">0</span><span class="sxs-lookup"><span data-stu-id="9b864-162">0</span></span> | <span data-ttu-id="9b864-163">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9b864-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="9b864-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b864-164">Remarks</span></span>

<span data-ttu-id="9b864-165">Tato funkce zalamuje volání na [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) metody.</span><span class="sxs-lookup"><span data-stu-id="9b864-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="9b864-166">Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9b864-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b864-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b864-167">Requirements</span></span>

<span data-ttu-id="9b864-168">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b864-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9b864-169">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9b864-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="9b864-170">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9b864-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9b864-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b864-171">See also</span></span>

- [<span data-ttu-id="9b864-172">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9b864-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
