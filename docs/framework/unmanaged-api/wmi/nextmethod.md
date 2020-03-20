---
title: NextMethod function (Unmanaged API Reference)
description: Funkce NextMethod načte další metodu ve výčtu.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174924"
---
# <a name="nextmethod-function"></a><span data-ttu-id="49db6-103">NextMethod</span><span class="sxs-lookup"><span data-stu-id="49db6-103">NextMethod function</span></span>
<span data-ttu-id="49db6-104">Načte další metodu ve výčtu, který začíná [voláníbeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="49db6-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="49db6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49db6-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="49db6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="49db6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="49db6-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="49db6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="49db6-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="49db6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="49db6-109">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="49db6-109">[in] Reserved.</span></span> <span data-ttu-id="49db6-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="49db6-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="49db6-111">[out] Ukazatel, který `null` odkazuje na před voláním.</span><span class="sxs-lookup"><span data-stu-id="49db6-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="49db6-112">Když funkce vrátí, adresa nového, `BSTR` který obsahuje název metody.</span><span class="sxs-lookup"><span data-stu-id="49db6-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="49db6-113">[out] Ukazatel, který obdrží ukazatel [na IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) který obsahuje `in` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="49db6-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="49db6-114">[out] Ukazatel, který obdrží ukazatel [na IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) který obsahuje `out` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="49db6-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="49db6-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="49db6-115">Return value</span></span>

<span data-ttu-id="49db6-116">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="49db6-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="49db6-117">Trvalé</span><span class="sxs-lookup"><span data-stu-id="49db6-117">Constant</span></span>  |<span data-ttu-id="49db6-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="49db6-118">Value</span></span>  |<span data-ttu-id="49db6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="49db6-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="49db6-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="49db6-120">0x8004101d</span></span> | <span data-ttu-id="49db6-121">Nebyla žádná výzva [`BeginEnumeration`](beginenumeration.md) k funkci.</span><span class="sxs-lookup"><span data-stu-id="49db6-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="49db6-122">0</span><span class="sxs-lookup"><span data-stu-id="49db6-122">0</span></span> | <span data-ttu-id="49db6-123">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="49db6-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="49db6-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="49db6-124">0x40005</span></span> | <span data-ttu-id="49db6-125">Neexistují žádné další vlastnosti ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="49db6-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="49db6-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49db6-126">Remarks</span></span>

<span data-ttu-id="49db6-127">Tato funkce zabalí volání metody [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)</span><span class="sxs-lookup"><span data-stu-id="49db6-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="49db6-128">Volající zahájí pořadí výčtu voláním funkce [BeginMethodEnumeration](beginmethodenumeration.md) a poté zavolá funkci [NextMethod], dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="49db6-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="49db6-129">Volitelně volající dokončí pořadí voláním [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="49db6-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="49db6-130">Volající může ukončit výčet brzy voláním [EndMethodEnumeration](endmethodenumeration.md) kdykoli.</span><span class="sxs-lookup"><span data-stu-id="49db6-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="49db6-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="49db6-131">Example</span></span>

<span data-ttu-id="49db6-132">Příklad jazyka C++ naleznete v metodě [IWbemClassObject::NextMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)</span><span class="sxs-lookup"><span data-stu-id="49db6-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49db6-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49db6-133">Requirements</span></span>  
 <span data-ttu-id="49db6-134">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49db6-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49db6-135">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="49db6-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="49db6-136">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49db6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49db6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="49db6-137">See also</span></span>

- [<span data-ttu-id="49db6-138">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="49db6-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
