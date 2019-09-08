---
title: PutInstanceWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce PutInstanceWmi vytvoří nebo aktualizuje instanci existující třídy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37810ecab2e02d4ec250dd2a4b2657c3b898f714
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798368"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="f0da7-103">PutInstanceWmi – funkce</span><span class="sxs-lookup"><span data-stu-id="f0da7-103">PutInstanceWmi function</span></span>

<span data-ttu-id="f0da7-104">Vytvoří nebo aktualizuje instanci existující třídy.</span><span class="sxs-lookup"><span data-stu-id="f0da7-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="f0da7-105">Instance je zapsána do úložiště rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="f0da7-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f0da7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0da7-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="f0da7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0da7-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="f0da7-108">pro Ukazatel na instanci, která má být zapsána.</span><span class="sxs-lookup"><span data-stu-id="f0da7-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="f0da7-109">pro Kombinace příznaků, které mají vliv na chování této funkce.</span><span class="sxs-lookup"><span data-stu-id="f0da7-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="f0da7-110">Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f0da7-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0da7-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f0da7-111">Constant</span></span>  |<span data-ttu-id="f0da7-112">Value</span><span class="sxs-lookup"><span data-stu-id="f0da7-112">Value</span></span>  |<span data-ttu-id="f0da7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f0da7-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="f0da7-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="f0da7-114">0x20000</span></span> | <span data-ttu-id="f0da7-115">Pokud je nastaveno, WMI neukládá žádné kvalifikátory se **změněným** charakterem.</span><span class="sxs-lookup"><span data-stu-id="f0da7-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="f0da7-116">Pokud není nastavena, předpokládá se, že tento objekt není lokalizován a že jsou všechny kvalifikátory uloženy s touto instancí.</span><span class="sxs-lookup"><span data-stu-id="f0da7-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="f0da7-117">0</span><span class="sxs-lookup"><span data-stu-id="f0da7-117">0</span></span> | <span data-ttu-id="f0da7-118">Vytvořte instanci, pokud neexistuje, nebo ji přepište, pokud už existuje.</span><span class="sxs-lookup"><span data-stu-id="f0da7-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="f0da7-119">1</span><span class="sxs-lookup"><span data-stu-id="f0da7-119">1</span></span> | <span data-ttu-id="f0da7-120">Aktualizujte instanci.</span><span class="sxs-lookup"><span data-stu-id="f0da7-120">Update the instance.</span></span> <span data-ttu-id="f0da7-121">Aby bylo volání úspěšné, musí instance existovat.</span><span class="sxs-lookup"><span data-stu-id="f0da7-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="f0da7-122">2</span><span class="sxs-lookup"><span data-stu-id="f0da7-122">2</span></span> | <span data-ttu-id="f0da7-123">Vytvořte instanci.</span><span class="sxs-lookup"><span data-stu-id="f0da7-123">Create the instance.</span></span> <span data-ttu-id="f0da7-124">Volání se nezdařilo, pokud instance již existuje.</span><span class="sxs-lookup"><span data-stu-id="f0da7-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="f0da7-125">0x10</span><span class="sxs-lookup"><span data-stu-id="f0da7-125">0x10</span></span> | <span data-ttu-id="f0da7-126">Příznak způsobí volání semisynchronní.</span><span class="sxs-lookup"><span data-stu-id="f0da7-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="f0da7-127">pro Obvykle je `null`tato hodnota.</span><span class="sxs-lookup"><span data-stu-id="f0da7-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="f0da7-128">V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.</span><span class="sxs-lookup"><span data-stu-id="f0da7-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="f0da7-129">mimo Pokud `null`je tento parametr nepoužitý.</span><span class="sxs-lookup"><span data-stu-id="f0da7-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="f0da7-130">Pokud `lFlags` `WBEM_S_NO_ERROR`obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce vrátí hodnotu okamžitě s.</span><span class="sxs-lookup"><span data-stu-id="f0da7-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="f0da7-131">Parametr obdrží ukazatel na nový objekt IWbemCallResult. [](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) `ppCallResult`</span><span class="sxs-lookup"><span data-stu-id="f0da7-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="f0da7-132">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f0da7-132">Return value</span></span>

<span data-ttu-id="f0da7-133">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f0da7-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f0da7-134">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f0da7-134">Constant</span></span>  |<span data-ttu-id="f0da7-135">Value</span><span class="sxs-lookup"><span data-stu-id="f0da7-135">Value</span></span>  |<span data-ttu-id="f0da7-136">Popis</span><span class="sxs-lookup"><span data-stu-id="f0da7-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="f0da7-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="f0da7-137">0x80041003</span></span> | <span data-ttu-id="f0da7-138">Uživatel nemá oprávnění k aktualizaci instance zadané třídy.</span><span class="sxs-lookup"><span data-stu-id="f0da7-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="f0da7-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f0da7-139">0x80041001</span></span> | <span data-ttu-id="f0da7-140">Došlo k neurčené chybě.</span><span class="sxs-lookup"><span data-stu-id="f0da7-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="f0da7-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="f0da7-141">0x80041010</span></span> | <span data-ttu-id="f0da7-142">Třída podporující tuto instanci není platná.</span><span class="sxs-lookup"><span data-stu-id="f0da7-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="f0da7-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="f0da7-143">0x80041028</span></span> | <span data-ttu-id="f0da7-144">byl zadán pro vlastnost, která nemůže být `null`, například ta, která je označena **indexovaným** nebo **Not_Null** kvalifikátorem. `null`</span><span class="sxs-lookup"><span data-stu-id="f0da7-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="f0da7-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="f0da7-145">0x8004100f</span></span> | <span data-ttu-id="f0da7-146">Zadaná instance není platná.</span><span class="sxs-lookup"><span data-stu-id="f0da7-146">The specified instance is not valid.</span></span> <span data-ttu-id="f0da7-147">(Například volání `PutInstanceWmi` pomocí třídy vrátí tuto hodnotu.)</span><span class="sxs-lookup"><span data-stu-id="f0da7-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f0da7-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f0da7-148">0x80041008</span></span> | <span data-ttu-id="f0da7-149">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="f0da7-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="f0da7-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="f0da7-150">0x80041019</span></span> | <span data-ttu-id="f0da7-151">`WBEM_FLAG_CREATE_ONLY` Příznak byl zadán, ale instance již existuje.</span><span class="sxs-lookup"><span data-stu-id="f0da7-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="f0da7-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f0da7-152">0x80041002</span></span> | <span data-ttu-id="f0da7-153">`WBEM_FLAG_UPDATE_ONLY`bylo zadáno v `lFlags`, ale instance neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f0da7-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f0da7-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f0da7-154">0x80041006</span></span> | <span data-ttu-id="f0da7-155">K dokončení této operace není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f0da7-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="f0da7-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="f0da7-156">0x80041033</span></span> | <span data-ttu-id="f0da7-157">Služba WMI byla pravděpodobně zastavena a restartována.</span><span class="sxs-lookup"><span data-stu-id="f0da7-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="f0da7-158">Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="f0da7-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f0da7-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f0da7-159">0x80041015</span></span> | <span data-ttu-id="f0da7-160">Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="f0da7-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f0da7-161">0</span><span class="sxs-lookup"><span data-stu-id="f0da7-161">0</span></span> | <span data-ttu-id="f0da7-162">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f0da7-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f0da7-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0da7-163">Remarks</span></span>

<span data-ttu-id="f0da7-164">Tato funkce zalomí volání metody [Služby IWbem::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .</span><span class="sxs-lookup"><span data-stu-id="f0da7-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="f0da7-165">`PutInstanceWmi` Funkce podporuje vytváření instancí a aktualizaci instancí stávajících tříd.</span><span class="sxs-lookup"><span data-stu-id="f0da7-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="f0da7-166">V závislosti na tom, `pCtx` jak je parametr nastavený, se aktualizují buď některé nebo všechny vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="f0da7-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="f0da7-167">Pokud instance, na kterou `pInst` ukazuje, patří do podtřídy, služba správy systému Windows volá všechny poskytovatele zodpovědné za třídy, ze kterých je odvozená podtřída.</span><span class="sxs-lookup"><span data-stu-id="f0da7-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="f0da7-168">Všechny tyto zprostředkovatele musí být úspěšné, aby původní `PutInstanceWmi` požadavek byl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="f0da7-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="f0da7-169">Zprostředkovatel podporující nejvyšší třídu v hierarchii je označován jako první.</span><span class="sxs-lookup"><span data-stu-id="f0da7-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="f0da7-170">Pořadí volání pokračuje s podtřídou nejvyšší třídy a pokračuje shora dolů, dokud Správa systému Windows nedosáhne poskytovatele pro třídu vlastnící instanci, na `pInst`kterou ukazuje.</span><span class="sxs-lookup"><span data-stu-id="f0da7-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="f0da7-171">Správa systému Windows nevolá poskytovatele pro žádnou z podřízených tříd instance.</span><span class="sxs-lookup"><span data-stu-id="f0da7-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="f0da7-172">Když aplikace musí aktualizovat instanci, která patří do hierarchie tříd, `pInst` parametr musí ukazovat na instanci obsahující vlastnosti, které mají být upraveny.</span><span class="sxs-lookup"><span data-stu-id="f0da7-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="f0da7-173">To znamená, že zvažte cílovou instanci, která patří do **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="f0da7-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="f0da7-174">Instance **ClassB** je odvozena z **třídy Class**a **Třída Class** definuje vlastnost **propa**.</span><span class="sxs-lookup"><span data-stu-id="f0da7-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="f0da7-175">Pokud aplikace chce provést změnu hodnoty **propa** v instanci **ClassB** , musí ji nastavit `pInst` na tuto instanci, nikoli na instanci **třídy Class**.</span><span class="sxs-lookup"><span data-stu-id="f0da7-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="f0da7-176">Volání `PutInstanceWmi` na instanci abstraktní třídy není povoleno.</span><span class="sxs-lookup"><span data-stu-id="f0da7-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="f0da7-177">Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="f0da7-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0da7-178">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0da7-178">Requirements</span></span>

<span data-ttu-id="f0da7-179">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0da7-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f0da7-180">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f0da7-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="f0da7-181">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0da7-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f0da7-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0da7-182">See also</span></span>

- [<span data-ttu-id="f0da7-183">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f0da7-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
