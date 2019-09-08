---
title: QualifierSet_Put – funkce (Reference nespravovaného rozhraní API)
description: Funkce QualifierSet_Put zapisuje pojmenovaný kvalifikátor a jeho hodnotu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798269"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="bf878-103">QualifierSet_Put – funkce</span><span class="sxs-lookup"><span data-stu-id="bf878-103">QualifierSet_Put function</span></span>

<span data-ttu-id="bf878-104">Zapíše pojmenovaný kvalifikátor a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bf878-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="bf878-105">Nový kvalifikátor přepíše předchozí hodnotu se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="bf878-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="bf878-106">Pokud kvalifikátor neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="bf878-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bf878-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf878-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="bf878-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf878-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="bf878-109">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="bf878-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="bf878-110">pro Ukazatel na instanci [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="bf878-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="bf878-111">pro Název kvalifikátoru, který se má zapsat</span><span class="sxs-lookup"><span data-stu-id="bf878-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="bf878-112">pro Ukazatel na platný `VARIANT` , který obsahuje kvalifikátor k zápisu.</span><span class="sxs-lookup"><span data-stu-id="bf878-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="bf878-113">Tento parametr nemůže být `null`.</span><span class="sxs-lookup"><span data-stu-id="bf878-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="bf878-114">pro Jedna z následujících konstant definující požadované charakter kvalifikátoru pro tento kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="bf878-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="bf878-115">Výchozí hodnota je `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="bf878-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="bf878-116">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf878-116">Constant</span></span>  |<span data-ttu-id="bf878-117">Value</span><span class="sxs-lookup"><span data-stu-id="bf878-117">Value</span></span>  |<span data-ttu-id="bf878-118">Popis</span><span class="sxs-lookup"><span data-stu-id="bf878-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="bf878-119">0</span><span class="sxs-lookup"><span data-stu-id="bf878-119">0</span></span> | <span data-ttu-id="bf878-120">Kvalifikátor lze přepsat v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="bf878-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="bf878-121">**Toto je výchozí hodnota.**</span><span class="sxs-lookup"><span data-stu-id="bf878-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="bf878-122">1</span><span class="sxs-lookup"><span data-stu-id="bf878-122">1</span></span> | <span data-ttu-id="bf878-123">Kvalifikátor je šířen do instancí.</span><span class="sxs-lookup"><span data-stu-id="bf878-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="bf878-124">2</span><span class="sxs-lookup"><span data-stu-id="bf878-124">2</span></span> | <span data-ttu-id="bf878-125">Kvalifikátor je šířen na odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="bf878-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="bf878-126">0x10</span><span class="sxs-lookup"><span data-stu-id="bf878-126">0x10</span></span> | <span data-ttu-id="bf878-127">Kvalifikátor nelze přepsat v odvozené třídě nebo instanci.</span><span class="sxs-lookup"><span data-stu-id="bf878-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="bf878-128">0x80</span><span class="sxs-lookup"><span data-stu-id="bf878-128">0x80</span></span> | <span data-ttu-id="bf878-129">Kvalifikátor je lokalizován.</span><span class="sxs-lookup"><span data-stu-id="bf878-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="bf878-130">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bf878-130">Return value</span></span>

<span data-ttu-id="bf878-131">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="bf878-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf878-132">Konstanta</span><span class="sxs-lookup"><span data-stu-id="bf878-132">Constant</span></span>  |<span data-ttu-id="bf878-133">Value</span><span class="sxs-lookup"><span data-stu-id="bf878-133">Value</span></span>  |<span data-ttu-id="bf878-134">Popis</span><span class="sxs-lookup"><span data-stu-id="bf878-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="bf878-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="bf878-135">0x8004101f</span></span> | <span data-ttu-id="bf878-136">Byl proveden Neplatný pokus o zadání kvalifikátoru **klíče** u vlastnosti, která nemůže být klíčem.</span><span class="sxs-lookup"><span data-stu-id="bf878-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="bf878-137">Klíče jsou zadány v definici třídy pro objekt a nelze je měnit na základě jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="bf878-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bf878-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bf878-138">0x80041008</span></span> | <span data-ttu-id="bf878-139">Parametr není platný.</span><span class="sxs-lookup"><span data-stu-id="bf878-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="bf878-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="bf878-140">0x80041029</span></span> | <span data-ttu-id="bf878-141">`pVal` Parametr není platným typem kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="bf878-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="bf878-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="bf878-142">0x8004101a</span></span> | <span data-ttu-id="bf878-143">Není možné volat `QualifierSet_Put` metodu na kvalifikátoru, protože vlastnící objekt nepovoluje přepsání.</span><span class="sxs-lookup"><span data-stu-id="bf878-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bf878-144">0</span><span class="sxs-lookup"><span data-stu-id="bf878-144">0</span></span> | <span data-ttu-id="bf878-145">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="bf878-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bf878-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf878-146">Remarks</span></span>

<span data-ttu-id="bf878-147">Tato funkce zalomí volání metody [IWbemQualifierSet::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .</span><span class="sxs-lookup"><span data-stu-id="bf878-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf878-148">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf878-148">Requirements</span></span>

<span data-ttu-id="bf878-149">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf878-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bf878-150">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf878-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="bf878-151">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf878-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bf878-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf878-152">See also</span></span>

- [<span data-ttu-id="bf878-153">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="bf878-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
