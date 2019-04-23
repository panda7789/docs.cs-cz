---
title: Funkce NextMethod (referenční dokumentace nespravovaného rozhraní API)
description: Funkce NextMethod načte další metody ve výčtu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3667f7371131a4c1394ba5ca619d1f605c89ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190883"
---
# <a name="nextmethod-function"></a><span data-ttu-id="9fb07-103">NextMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="9fb07-103">NextMethod function</span></span>
<span data-ttu-id="9fb07-104">Načte další metody ve výčtu, která začíná volání [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9fb07-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9fb07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fb07-105">Syntax</span></span>  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="9fb07-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fb07-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9fb07-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="9fb07-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9fb07-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="9fb07-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="9fb07-109">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="9fb07-109">[in] Reserved.</span></span> <span data-ttu-id="9fb07-110">Tento parametr musí být 0.</span><span class="sxs-lookup"><span data-stu-id="9fb07-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="9fb07-111">[out] Ukazatel, který odkazuje na `null` před voláním.</span><span class="sxs-lookup"><span data-stu-id="9fb07-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="9fb07-112">Pokud funkce vrátí, adresa nového `BSTR` obsahující název metody.</span><span class="sxs-lookup"><span data-stu-id="9fb07-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="9fb07-113">[out] Ukazatel, který přijímá ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `in` parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="9fb07-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="9fb07-114">[out] Ukazatel, který přijímá ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `out` parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="9fb07-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="9fb07-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9fb07-115">Return value</span></span>

<span data-ttu-id="9fb07-116">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="9fb07-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9fb07-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="9fb07-117">Constant</span></span>  |<span data-ttu-id="9fb07-118">Value</span><span class="sxs-lookup"><span data-stu-id="9fb07-118">Value</span></span>  |<span data-ttu-id="9fb07-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9fb07-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="9fb07-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="9fb07-120">0x8004101d</span></span> | <span data-ttu-id="9fb07-121">Došlo bez volání [ `BeginEnumeration` ](beginenumeration.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9fb07-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9fb07-122">0</span><span class="sxs-lookup"><span data-stu-id="9fb07-122">0</span></span> | <span data-ttu-id="9fb07-123">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9fb07-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="9fb07-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="9fb07-124">0x40005</span></span> | <span data-ttu-id="9fb07-125">Nejsou žádné další vlastnosti ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="9fb07-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="9fb07-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fb07-126">Remarks</span></span>

<span data-ttu-id="9fb07-127">Tato funkce zalamuje volání na [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="9fb07-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="9fb07-128">Volající začne pořadí výčtu voláním [BeginMethodEnumeration](beginmethodenumeration.md) pracovat a pak volá funkci [NextMethod], dokud se funkce vrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="9fb07-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="9fb07-129">Volitelně můžete volající dokončení sekvence pomocí volání [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9fb07-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="9fb07-130">Volající může již v rané fázi ukončit výčtu voláním [EndMethodEnumeration](endmethodenumeration.md) kdykoli.</span><span class="sxs-lookup"><span data-stu-id="9fb07-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="9fb07-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="9fb07-131">Example</span></span>

<span data-ttu-id="9fb07-132">Příklad C++, naleznete v tématu [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.</span><span class="sxs-lookup"><span data-stu-id="9fb07-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9fb07-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fb07-133">Requirements</span></span>  
 <span data-ttu-id="9fb07-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb07-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb07-135">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9fb07-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9fb07-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb07-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb07-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fb07-137">See also</span></span>

- [<span data-ttu-id="9fb07-138">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="9fb07-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
