---
title: CreateClassEnumWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce CreateClassEnumWmi vrací enumerátor pro všechny třídy, které odpovídají zadaným kritériím.
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
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798740"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="6b8cf-103">CreateClassEnumWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="6b8cf-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="6b8cf-104">Vrátí enumerátor pro všechny třídy, které odpovídají zadaným kritériím výběru.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6b8cf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b8cf-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="6b8cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b8cf-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="6b8cf-107">pro Pokud není `null` nebo prázdné, určuje název nadřazené třídy; enumerátor vrátí pouze podtřídy této třídy.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="6b8cf-108">Pokud je `null` nebo prázdný a `lFlags` je WBEM_FLAG_SHALLOW, vrátí pouze třídy nejvyšší úrovně (třídy bez nadřazené třídy).</span><span class="sxs-lookup"><span data-stu-id="6b8cf-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="6b8cf-109">Pokud je `null` nebo prázdný a `lFlags` je `WBEM_FLAG_DEEP`, vrátí všechny třídy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="6b8cf-110">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6b8cf-111">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="6b8cf-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6b8cf-112">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6b8cf-112">Constant</span></span>  |<span data-ttu-id="6b8cf-113">Value</span><span class="sxs-lookup"><span data-stu-id="6b8cf-113">Value</span></span>  |<span data-ttu-id="6b8cf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6b8cf-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6b8cf-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="6b8cf-115">0x20000</span></span> | <span data-ttu-id="6b8cf-116">Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="6b8cf-117">Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="6b8cf-118">0</span><span class="sxs-lookup"><span data-stu-id="6b8cf-118">0</span></span> | <span data-ttu-id="6b8cf-119">Výčet zahrnuje všechny podtřídy v hierarchii, ale ne tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="6b8cf-120">1</span><span class="sxs-lookup"><span data-stu-id="6b8cf-120">1</span></span> | <span data-ttu-id="6b8cf-121">Výčet zahrnuje pouze čistě instance této třídy a vyloučí všechny instance podtříd, které poskytují vlastnosti, které se v této třídě nenašly.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6b8cf-122">0x10</span><span class="sxs-lookup"><span data-stu-id="6b8cf-122">0x10</span></span> | <span data-ttu-id="6b8cf-123">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="6b8cf-124">0x20</span><span class="sxs-lookup"><span data-stu-id="6b8cf-124">0x20</span></span> | <span data-ttu-id="6b8cf-125">Funkce vrátí enumerátor pouze s dopředné.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="6b8cf-126">Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cf-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="6b8cf-127">0</span><span class="sxs-lookup"><span data-stu-id="6b8cf-127">0</span></span> | <span data-ttu-id="6b8cf-128">Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="6b8cf-129">Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="6b8cf-130">pro Obvykle je `null`tato hodnota.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6b8cf-131">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="6b8cf-132">mimo Přijme ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="6b8cf-133">pro Úroveň autorizace.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="6b8cf-134">pro Úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="6b8cf-135">pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="6b8cf-136">pro Uživatelské jméno</span><span class="sxs-lookup"><span data-stu-id="6b8cf-136">[in] The user name.</span></span> <span data-ttu-id="6b8cf-137">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="6b8cf-138">pro Heslo.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-138">[in] The password.</span></span> <span data-ttu-id="6b8cf-139">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="6b8cf-140">pro Název domény uživatele</span><span class="sxs-lookup"><span data-stu-id="6b8cf-140">[in] The domain name of the user.</span></span> <span data-ttu-id="6b8cf-141">Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b8cf-142">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b8cf-142">Return value</span></span>

<span data-ttu-id="6b8cf-143">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="6b8cf-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6b8cf-144">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6b8cf-144">Constant</span></span>  |<span data-ttu-id="6b8cf-145">Value</span><span class="sxs-lookup"><span data-stu-id="6b8cf-145">Value</span></span>  |<span data-ttu-id="6b8cf-146">Popis</span><span class="sxs-lookup"><span data-stu-id="6b8cf-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6b8cf-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="6b8cf-147">0x80041003</span></span> | <span data-ttu-id="6b8cf-148">Uživatel nemá oprávnění k zobrazení jedné nebo více tříd, které může funkce vracet.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6b8cf-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6b8cf-149">0x80041001</span></span> | <span data-ttu-id="6b8cf-150">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="6b8cf-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="6b8cf-151">0x80041010</span></span> | <span data-ttu-id="6b8cf-152">`strSuperClass`neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6b8cf-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6b8cf-153">0x80041008</span></span> | <span data-ttu-id="6b8cf-154">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6b8cf-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6b8cf-155">0x80041006</span></span> | <span data-ttu-id="6b8cf-156">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6b8cf-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6b8cf-157">0x80041033</span></span> | <span data-ttu-id="6b8cf-158">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6b8cf-159">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6b8cf-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6b8cf-160">0x80041015</span></span> | <span data-ttu-id="6b8cf-161">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6b8cf-162">0</span><span class="sxs-lookup"><span data-stu-id="6b8cf-162">0</span></span> | <span data-ttu-id="6b8cf-163">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6b8cf-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6b8cf-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b8cf-164">Remarks</span></span>

<span data-ttu-id="6b8cf-165">Tato funkce zalomí volání metody [Služby IWbem:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="6b8cf-166">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6b8cf-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6b8cf-167">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b8cf-167">Requirements</span></span>

<span data-ttu-id="6b8cf-168">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b8cf-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6b8cf-169">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6b8cf-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6b8cf-170">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6b8cf-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6b8cf-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b8cf-171">See also</span></span>

- [<span data-ttu-id="6b8cf-172">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6b8cf-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
