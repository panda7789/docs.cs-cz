---
title: CreateInstanceEnumWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce CreateInstanceEnumWmi vrací enumerátor obsahující instance zadané třídy, které splňují kritéria výběru.
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
ms.openlocfilehash: 9ffa718be0e8b67471fdf8cb277df201388d2840
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130407"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="ad17c-103">CreateInstanceEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="ad17c-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="ad17c-104">Vrátí enumerátor, který vrátí instance zadané třídy, které splňují zadaná kritéria výběru.</span><span class="sxs-lookup"><span data-stu-id="ad17c-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ad17c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad17c-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="ad17c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad17c-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="ad17c-107">pro Název třídy, pro kterou jsou požadovány instance.</span><span class="sxs-lookup"><span data-stu-id="ad17c-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="ad17c-108">Tento parametr nelze `null`.</span><span class="sxs-lookup"><span data-stu-id="ad17c-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="ad17c-109">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="ad17c-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="ad17c-110">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ad17c-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ad17c-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ad17c-111">Constant</span></span>  |<span data-ttu-id="ad17c-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ad17c-112">Value</span></span>  |<span data-ttu-id="ad17c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ad17c-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="ad17c-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="ad17c-114">0x20000</span></span> | <span data-ttu-id="ad17c-115">Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="ad17c-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="ad17c-116">Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ad17c-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="ad17c-117">0,8</span><span class="sxs-lookup"><span data-stu-id="ad17c-117">0</span></span> | <span data-ttu-id="ad17c-118">Výčet obsahuje tuto a všechny podtřídy v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="ad17c-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="ad17c-119">první</span><span class="sxs-lookup"><span data-stu-id="ad17c-119">1</span></span> | <span data-ttu-id="ad17c-120">Výčet zahrnuje pouze čistě instance této třídy a vyloučí všechny instance podtříd, které poskytují vlastnosti, které se v této třídě nenašly.</span><span class="sxs-lookup"><span data-stu-id="ad17c-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="ad17c-121">0x10</span><span class="sxs-lookup"><span data-stu-id="ad17c-121">0x10</span></span> | <span data-ttu-id="ad17c-122">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="ad17c-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="ad17c-123">0x20</span><span class="sxs-lookup"><span data-stu-id="ad17c-123">0x20</span></span> | <span data-ttu-id="ad17c-124">Funkce vrátí enumerátor pouze s dopředné.</span><span class="sxs-lookup"><span data-stu-id="ad17c-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="ad17c-125">Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="ad17c-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="ad17c-126">0,8</span><span class="sxs-lookup"><span data-stu-id="ad17c-126">0</span></span> | <span data-ttu-id="ad17c-127">Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="ad17c-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="ad17c-128">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="ad17c-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="ad17c-129">pro Tato hodnota je obvykle `null`.</span><span class="sxs-lookup"><span data-stu-id="ad17c-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="ad17c-130">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované instance.</span><span class="sxs-lookup"><span data-stu-id="ad17c-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="ad17c-131">mimo Přijme ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ad17c-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="ad17c-132">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="ad17c-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="ad17c-133">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="ad17c-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="ad17c-134">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ad17c-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="ad17c-135">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="ad17c-135">[in] The user name.</span></span> <span data-ttu-id="ad17c-136">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="ad17c-137">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="ad17c-137">[in] The password.</span></span> <span data-ttu-id="ad17c-138">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="ad17c-139">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="ad17c-139">[in] The domain name of the user.</span></span> <span data-ttu-id="ad17c-140">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad17c-141">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad17c-141">Return value</span></span>

<span data-ttu-id="ad17c-142">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="ad17c-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ad17c-143">Konstanta</span><span class="sxs-lookup"><span data-stu-id="ad17c-143">Constant</span></span>  |<span data-ttu-id="ad17c-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ad17c-144">Value</span></span>  |<span data-ttu-id="ad17c-145">Popis</span><span class="sxs-lookup"><span data-stu-id="ad17c-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="ad17c-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="ad17c-146">0x80041003</span></span> | <span data-ttu-id="ad17c-147">Uživatel nemá oprávnění k zobrazení instancí zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="ad17c-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="ad17c-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ad17c-148">0x80041001</span></span> | <span data-ttu-id="ad17c-149">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="ad17c-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="ad17c-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="ad17c-150">0x80041010</span></span> | <span data-ttu-id="ad17c-151">`strFilter` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ad17c-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ad17c-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ad17c-152">0x80041008</span></span> | <span data-ttu-id="ad17c-153">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="ad17c-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ad17c-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ad17c-154">0x80041006</span></span> | <span data-ttu-id="ad17c-155">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="ad17c-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="ad17c-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="ad17c-156">0x80041033</span></span> | <span data-ttu-id="ad17c-157">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="ad17c-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="ad17c-158">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="ad17c-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="ad17c-159">0x80041015</span></span> | <span data-ttu-id="ad17c-160">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ad17c-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ad17c-161">0,8</span><span class="sxs-lookup"><span data-stu-id="ad17c-161">0</span></span> | <span data-ttu-id="ad17c-162">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="ad17c-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ad17c-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad17c-163">Remarks</span></span>

<span data-ttu-id="ad17c-164">Tato funkce zalomí volání metody [Služby IWbem:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="ad17c-165">Všimněte si, že vrácený enumerátor může mít nula prvků.</span><span class="sxs-lookup"><span data-stu-id="ad17c-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="ad17c-166">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="ad17c-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad17c-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad17c-167">Requirements</span></span>

<span data-ttu-id="ad17c-168">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad17c-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ad17c-169">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ad17c-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ad17c-170">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ad17c-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ad17c-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad17c-171">See also</span></span>

- [<span data-ttu-id="ad17c-172">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="ad17c-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
