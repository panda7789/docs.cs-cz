---
title: PutClassWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje stávající.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101781"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="a8c25-103">PutClassWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="a8c25-103">PutClassWmi function</span></span>

<span data-ttu-id="a8c25-104">Vytvoří novou třídu nebo aktualizuje stávající.</span><span class="sxs-lookup"><span data-stu-id="a8c25-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a8c25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8c25-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="a8c25-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8c25-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="a8c25-107">pro Ukazatel na platnou definici třídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="a8c25-108">Musí být správně inicializován se všemi požadovanými hodnotami vlastností.</span><span class="sxs-lookup"><span data-stu-id="a8c25-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="a8c25-109">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="a8c25-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="a8c25-110">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a8c25-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a8c25-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a8c25-111">Constant</span></span>  |<span data-ttu-id="a8c25-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8c25-112">Value</span></span>  |<span data-ttu-id="a8c25-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a8c25-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="a8c25-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="a8c25-114">0x20000</span></span> | <span data-ttu-id="a8c25-115">Pokud je nastaveno, WMI neukládá žádné kvalifikátory se změněným charakterem.</span><span class="sxs-lookup"><span data-stu-id="a8c25-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="a8c25-116">Pokud není nastavena, předpokládá se, že tento objekt není lokalizován a že jsou všechny kvalifikátory uloženy s touto instancí.</span><span class="sxs-lookup"><span data-stu-id="a8c25-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="a8c25-117">0,8</span><span class="sxs-lookup"><span data-stu-id="a8c25-117">0</span></span> | <span data-ttu-id="a8c25-118">Vytvořte třídu, pokud neexistuje, nebo ji přepište, pokud již existuje.</span><span class="sxs-lookup"><span data-stu-id="a8c25-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="a8c25-119">první</span><span class="sxs-lookup"><span data-stu-id="a8c25-119">1</span></span> | <span data-ttu-id="a8c25-120">Aktualizujte třídu.</span><span class="sxs-lookup"><span data-stu-id="a8c25-120">Update the class.</span></span> <span data-ttu-id="a8c25-121">Aby bylo volání úspěšné, musí třída existovat.</span><span class="sxs-lookup"><span data-stu-id="a8c25-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="a8c25-122">odst</span><span class="sxs-lookup"><span data-stu-id="a8c25-122">2</span></span> | <span data-ttu-id="a8c25-123">Vytvořte třídu.</span><span class="sxs-lookup"><span data-stu-id="a8c25-123">Create the class.</span></span> <span data-ttu-id="a8c25-124">Volání se nezdařilo, pokud již třída existuje.</span><span class="sxs-lookup"><span data-stu-id="a8c25-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="a8c25-125">0x10</span><span class="sxs-lookup"><span data-stu-id="a8c25-125">0x10</span></span> | <span data-ttu-id="a8c25-126">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="a8c25-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="a8c25-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="a8c25-127">0x10000</span></span> | <span data-ttu-id="a8c25-128">Poskytovatelé nabízených oznámení musí zadat tento příznak při volání `PutClassWmi` k označení toho, že se tato třída změnila.</span><span class="sxs-lookup"><span data-stu-id="a8c25-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="a8c25-129">0,8</span><span class="sxs-lookup"><span data-stu-id="a8c25-129">0</span></span> | <span data-ttu-id="a8c25-130">Umožňuje aktualizovat třídu, pokud nejsou žádné odvozené třídy a žádné instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="a8c25-131">Také umožňuje aktualizace ve všech případech, pokud je změna pouze neimportované kvalifikátory, jako je například kvalifikátor Description.</span><span class="sxs-lookup"><span data-stu-id="a8c25-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="a8c25-132">Pokud má třída instance nebo změny důležité kvalifikátory, aktualizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="a8c25-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="a8c25-133">0x20</span><span class="sxs-lookup"><span data-stu-id="a8c25-133">0x20</span></span> | <span data-ttu-id="a8c25-134">Umožňuje aktualizace tříd i v případě, že existují podřízené třídy, pokud změna nezpůsobí konflikty s podřízenými třídami.</span><span class="sxs-lookup"><span data-stu-id="a8c25-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="a8c25-135">Tento příznak například umožňuje přidat novou vlastnost do základní třídy, která nebyla dříve uvedena v žádné z podřízených tříd.</span><span class="sxs-lookup"><span data-stu-id="a8c25-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="a8c25-136">Pokud má třída instance, aktualizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="a8c25-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="a8c25-137">0x40</span><span class="sxs-lookup"><span data-stu-id="a8c25-137">0x40</span></span> | <span data-ttu-id="a8c25-138">vynutí aktualizace tříd, pokud existují konfliktní podřízené třídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="a8c25-139">Například tento příznak vynutí aktualizaci, pokud je kvalifikátor třídy definován v podřízené třídě a základní třída se pokusí přidat stejný kvalifikátor, který je v konfliktu s existujícím.</span><span class="sxs-lookup"><span data-stu-id="a8c25-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="a8c25-140">V režimu vynucení tis konflikt je vyřešen odstraněním kolidujícího kvalifikátoru v podřízené třídě.</span><span class="sxs-lookup"><span data-stu-id="a8c25-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="a8c25-141">pro Tato hodnota je obvykle `null`.</span><span class="sxs-lookup"><span data-stu-id="a8c25-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="a8c25-142">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="a8c25-143">mimo Pokud `null`, tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="a8c25-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="a8c25-144">Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce se vrátí hned `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="a8c25-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="a8c25-145">Parametr `ppCallResult` přijme ukazatel na nový objekt [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="a8c25-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8c25-146">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8c25-146">Return value</span></span>

<span data-ttu-id="a8c25-147">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="a8c25-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a8c25-148">Konstanta</span><span class="sxs-lookup"><span data-stu-id="a8c25-148">Constant</span></span>  |<span data-ttu-id="a8c25-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8c25-149">Value</span></span>  |<span data-ttu-id="a8c25-150">Popis</span><span class="sxs-lookup"><span data-stu-id="a8c25-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="a8c25-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="a8c25-151">0x80041003</span></span> | <span data-ttu-id="a8c25-152">Uživatel nemá oprávnění k vytváření nebo změnám tříd.</span><span class="sxs-lookup"><span data-stu-id="a8c25-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="a8c25-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a8c25-153">0x80041001</span></span> | <span data-ttu-id="a8c25-154">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="a8c25-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="a8c25-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="a8c25-155">0x80041010</span></span> | <span data-ttu-id="a8c25-156">Zadaná třída není platná.</span><span class="sxs-lookup"><span data-stu-id="a8c25-156">The specified class is not valid.</span></span> <span data-ttu-id="a8c25-157">Obvykle to znamená, že `pObject` určuje objekt instance.</span><span class="sxs-lookup"><span data-stu-id="a8c25-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a8c25-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a8c25-158">0x80041008</span></span> | <span data-ttu-id="a8c25-159">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="a8c25-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="a8c25-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="a8c25-160">0x80041016</span></span> | <span data-ttu-id="a8c25-161">Zadaný název třídy není platný.</span><span class="sxs-lookup"><span data-stu-id="a8c25-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="a8c25-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="a8c25-162">0x80041025</span></span> | <span data-ttu-id="a8c25-163">Byl proveden pokus o provedení změny, která by způsobila neplatnost podtřídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="a8c25-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="a8c25-164">0x80041019</span></span> | <span data-ttu-id="a8c25-165">Byl zadán příznak `WBEM_FLAG_CREATE_ONLY`, ale třída již existuje.</span><span class="sxs-lookup"><span data-stu-id="a8c25-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="a8c25-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a8c25-166">0x80041002</span></span> | <span data-ttu-id="a8c25-167">`WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`a Třída nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="a8c25-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="a8c25-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="a8c25-168">0x80041020</span></span> | <span data-ttu-id="a8c25-169">Nebyly nastaveny všechny požadované vlastnosti pro třídy.</span><span class="sxs-lookup"><span data-stu-id="a8c25-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a8c25-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a8c25-170">0x80041006</span></span> | <span data-ttu-id="a8c25-171">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="a8c25-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="a8c25-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="a8c25-172">0x80041033</span></span> | <span data-ttu-id="a8c25-173">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="a8c25-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="a8c25-174">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="a8c25-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="a8c25-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="a8c25-175">0x80041015</span></span> | <span data-ttu-id="a8c25-176">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="a8c25-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a8c25-177">0,8</span><span class="sxs-lookup"><span data-stu-id="a8c25-177">0</span></span> | <span data-ttu-id="a8c25-178">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a8c25-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a8c25-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8c25-179">Remarks</span></span>

<span data-ttu-id="a8c25-180">Tato funkce zalomí volání metody [Služby IWbem::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .</span><span class="sxs-lookup"><span data-stu-id="a8c25-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="a8c25-181">Uživatel nemůže vytvořit třídy s názvy, které začínají nebo končí znakem podtržítka.</span><span class="sxs-lookup"><span data-stu-id="a8c25-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="a8c25-182">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="a8c25-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8c25-183">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8c25-183">Requirements</span></span>

<span data-ttu-id="a8c25-184">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c25-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a8c25-185">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="a8c25-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a8c25-186">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c25-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a8c25-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8c25-187">See also</span></span>

- [<span data-ttu-id="a8c25-188">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="a8c25-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
