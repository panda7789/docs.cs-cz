---
title: EndMethodEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce EndMethodEnumeration ukončí sekvenci výčtu metody.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 174cf76d4b0ddf07e67e02bff20a983dca08819a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132023"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="37228-103">Funkce EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="37228-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="37228-104">Ukončí sekvenci výčtu spuštěnou voláním [funkce BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="37228-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="37228-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37228-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="37228-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37228-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="37228-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="37228-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="37228-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="37228-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="37228-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37228-109">Return value</span></span>

<span data-ttu-id="37228-110">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="37228-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="37228-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="37228-111">Constant</span></span>  |<span data-ttu-id="37228-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37228-112">Value</span></span>  |<span data-ttu-id="37228-113">Popis</span><span class="sxs-lookup"><span data-stu-id="37228-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="37228-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="37228-114">0x8004101d</span></span> | <span data-ttu-id="37228-115">Došlo k vnitřní chybě.</span><span class="sxs-lookup"><span data-stu-id="37228-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="37228-116">0,8</span><span class="sxs-lookup"><span data-stu-id="37228-116">0</span></span> | <span data-ttu-id="37228-117">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="37228-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="37228-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37228-118">Remarks</span></span>

<span data-ttu-id="37228-119">Tato funkce zalomí volání metody [IWbemclassObject:: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="37228-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="37228-120">Volající zahájí sekvenci výčtu pomocí [funkce BeginMethodEnumeration](beginmethodenumeration.md)a poté zavolá [funkci NextMethod](nextmethod.md ), dokud metoda nevrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="37228-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="37228-121">Volající volitelně dokončí sekvenci voláním `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="37228-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="37228-122">Volající může ukončit výčet hned po volání `EndMethodEnumeration` kdykoli.</span><span class="sxs-lookup"><span data-stu-id="37228-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="37228-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37228-123">Requirements</span></span>  
 <span data-ttu-id="37228-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37228-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37228-125">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="37228-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="37228-126">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37228-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37228-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37228-127">See also</span></span>

- [<span data-ttu-id="37228-128">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="37228-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
