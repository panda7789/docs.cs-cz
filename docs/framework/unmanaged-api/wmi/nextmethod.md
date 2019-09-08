---
title: NextMethod – funkce (Reference nespravovaného rozhraní API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee743a4499824bea723043d5a2c7d57d7cbd7106
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798431"
---
# <a name="nextmethod-function"></a><span data-ttu-id="4db0e-103">NextMethod – funkce</span><span class="sxs-lookup"><span data-stu-id="4db0e-103">NextMethod function</span></span>
<span data-ttu-id="4db0e-104">Načte další metodu ve výčtu, který začíná voláním [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4db0e-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4db0e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4db0e-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="4db0e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4db0e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4db0e-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4db0e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4db0e-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="4db0e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="4db0e-109">pro Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="4db0e-109">[in] Reserved.</span></span> <span data-ttu-id="4db0e-110">Tento parametr musí mít hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="4db0e-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="4db0e-111">mimo Ukazatel, na `null` který odkazuje před voláním.</span><span class="sxs-lookup"><span data-stu-id="4db0e-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="4db0e-112">Když se funkce vrátí, adresa nového `BSTR` obsahující název metody.</span><span class="sxs-lookup"><span data-stu-id="4db0e-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="4db0e-113">mimo Ukazatel, který obdrží ukazatel na [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `in` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4db0e-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="4db0e-114">mimo Ukazatel, který obdrží ukazatel na [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , který obsahuje `out` parametry pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4db0e-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4db0e-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4db0e-115">Return value</span></span>

<span data-ttu-id="4db0e-116">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="4db0e-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4db0e-117">Konstanta</span><span class="sxs-lookup"><span data-stu-id="4db0e-117">Constant</span></span>  |<span data-ttu-id="4db0e-118">Value</span><span class="sxs-lookup"><span data-stu-id="4db0e-118">Value</span></span>  |<span data-ttu-id="4db0e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="4db0e-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="4db0e-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="4db0e-120">0x8004101d</span></span> | <span data-ttu-id="4db0e-121">[`BeginEnumeration`](beginenumeration.md) Funkci se nevolalo.</span><span class="sxs-lookup"><span data-stu-id="4db0e-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="4db0e-122">0</span><span class="sxs-lookup"><span data-stu-id="4db0e-122">0</span></span> | <span data-ttu-id="4db0e-123">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="4db0e-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="4db0e-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="4db0e-124">0x40005</span></span> | <span data-ttu-id="4db0e-125">Ve výčtu nejsou žádné další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4db0e-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="4db0e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4db0e-126">Remarks</span></span>

<span data-ttu-id="4db0e-127">Tato funkce zalomí volání metody [IWbemclassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="4db0e-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="4db0e-128">Volající zahájí sekvenci výčtu voláním funkce [BeginMethodEnumeration](beginmethodenumeration.md) a poté zavolá funkci [NextMethod], dokud funkce nevrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="4db0e-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="4db0e-129">Volitelně volající sekvenci dokončí voláním [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4db0e-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="4db0e-130">Volající může ukončit výčet na začátku voláním [EndMethodEnumeration](endmethodenumeration.md) v každém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="4db0e-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="4db0e-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="4db0e-131">Example</span></span>

<span data-ttu-id="4db0e-132">C++ Příklad naleznete v tématu metoda [IWbemclassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="4db0e-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4db0e-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4db0e-133">Requirements</span></span>  
 <span data-ttu-id="4db0e-134">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4db0e-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4db0e-135">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4db0e-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4db0e-136">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4db0e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db0e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4db0e-137">See also</span></span>

- [<span data-ttu-id="4db0e-138">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="4db0e-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
