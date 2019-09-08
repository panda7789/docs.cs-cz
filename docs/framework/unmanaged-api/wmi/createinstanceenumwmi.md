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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7709d9c50a494013ece2f91b3acc213278f0e57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798901"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="6c6af-103">CreateInstanceEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="6c6af-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="6c6af-104">Vrátí enumerátor, který vrátí instance zadané třídy, které splňují zadaná kritéria výběru.</span><span class="sxs-lookup"><span data-stu-id="6c6af-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6c6af-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c6af-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="6c6af-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c6af-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="6c6af-107">pro Název třídy, pro kterou jsou požadovány instance.</span><span class="sxs-lookup"><span data-stu-id="6c6af-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="6c6af-108">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="6c6af-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="6c6af-109">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="6c6af-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6c6af-110">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="6c6af-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6c6af-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6c6af-111">Constant</span></span>  |<span data-ttu-id="6c6af-112">Value</span><span class="sxs-lookup"><span data-stu-id="6c6af-112">Value</span></span>  |<span data-ttu-id="6c6af-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6c6af-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6c6af-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="6c6af-114">0x20000</span></span> | <span data-ttu-id="6c6af-115">Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="6c6af-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="6c6af-116">Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6c6af-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="6c6af-117">0</span><span class="sxs-lookup"><span data-stu-id="6c6af-117">0</span></span> | <span data-ttu-id="6c6af-118">Výčet obsahuje tuto a všechny podtřídy v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="6c6af-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="6c6af-119">1</span><span class="sxs-lookup"><span data-stu-id="6c6af-119">1</span></span> | <span data-ttu-id="6c6af-120">Výčet zahrnuje pouze čistě instance této třídy a vyloučí všechny instance podtříd, které poskytují vlastnosti, které se v této třídě nenašly.</span><span class="sxs-lookup"><span data-stu-id="6c6af-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6c6af-121">0x10</span><span class="sxs-lookup"><span data-stu-id="6c6af-121">0x10</span></span> | <span data-ttu-id="6c6af-122">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="6c6af-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="6c6af-123">0x20</span><span class="sxs-lookup"><span data-stu-id="6c6af-123">0x20</span></span> | <span data-ttu-id="6c6af-124">Funkce vrátí enumerátor pouze s dopředné.</span><span class="sxs-lookup"><span data-stu-id="6c6af-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="6c6af-125">Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="6c6af-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="6c6af-126">0</span><span class="sxs-lookup"><span data-stu-id="6c6af-126">0</span></span> | <span data-ttu-id="6c6af-127">Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="6c6af-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="6c6af-128">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="6c6af-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="6c6af-129">pro Obvykle je `null`tato hodnota.</span><span class="sxs-lookup"><span data-stu-id="6c6af-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6c6af-130">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované instance.</span><span class="sxs-lookup"><span data-stu-id="6c6af-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="6c6af-131">mimo Přijme ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6c6af-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="6c6af-132">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="6c6af-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="6c6af-133">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="6c6af-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="6c6af-134">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6c6af-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="6c6af-135">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="6c6af-135">[in] The user name.</span></span> <span data-ttu-id="6c6af-136">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="6c6af-137">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="6c6af-137">[in] The password.</span></span> <span data-ttu-id="6c6af-138">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="6c6af-139">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="6c6af-139">[in] The domain name of the user.</span></span> <span data-ttu-id="6c6af-140">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6c6af-141">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c6af-141">Return value</span></span>

<span data-ttu-id="6c6af-142">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="6c6af-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6c6af-143">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6c6af-143">Constant</span></span>  |<span data-ttu-id="6c6af-144">Value</span><span class="sxs-lookup"><span data-stu-id="6c6af-144">Value</span></span>  |<span data-ttu-id="6c6af-145">Popis</span><span class="sxs-lookup"><span data-stu-id="6c6af-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6c6af-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="6c6af-146">0x80041003</span></span> | <span data-ttu-id="6c6af-147">Uživatel nemá oprávnění k zobrazení instancí zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="6c6af-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6c6af-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6c6af-148">0x80041001</span></span> | <span data-ttu-id="6c6af-149">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="6c6af-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="6c6af-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="6c6af-150">0x80041010</span></span> | <span data-ttu-id="6c6af-151">`strFilter`neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6c6af-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6c6af-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6c6af-152">0x80041008</span></span> | <span data-ttu-id="6c6af-153">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="6c6af-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6c6af-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6c6af-154">0x80041006</span></span> | <span data-ttu-id="6c6af-155">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6c6af-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6c6af-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6c6af-156">0x80041033</span></span> | <span data-ttu-id="6c6af-157">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="6c6af-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6c6af-158">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6c6af-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6c6af-159">0x80041015</span></span> | <span data-ttu-id="6c6af-160">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6c6af-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6c6af-161">0</span><span class="sxs-lookup"><span data-stu-id="6c6af-161">0</span></span> | <span data-ttu-id="6c6af-162">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6c6af-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6c6af-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c6af-163">Remarks</span></span>

<span data-ttu-id="6c6af-164">Tato funkce zalomí volání metody [Služby IWbem:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="6c6af-165">Všimněte si, že vrácený enumerátor může mít nula prvků.</span><span class="sxs-lookup"><span data-stu-id="6c6af-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="6c6af-166">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6c6af-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c6af-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c6af-167">Requirements</span></span>

<span data-ttu-id="6c6af-168">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6af-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6c6af-169">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6c6af-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6c6af-170">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6af-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6c6af-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c6af-171">See also</span></span>

- [<span data-ttu-id="6c6af-172">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6c6af-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
