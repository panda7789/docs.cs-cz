---
title: Funkce EndMethodEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce EndMethodEnumeration ukončí sekvenci – metoda výčtu.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7f29c365e9f6ba85f85ceb232f7af89446af2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040596"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="f5e9c-103">Funkce EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="f5e9c-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="f5e9c-104">Ukončí sekvenci výčet začít volání [funkce BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f5e9c-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f5e9c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5e9c-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f5e9c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5e9c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f5e9c-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f5e9c-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5e9c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5e9c-109">Return value</span></span>

<span data-ttu-id="f5e9c-110">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f5e9c-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f5e9c-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f5e9c-111">Constant</span></span>  |<span data-ttu-id="f5e9c-112">Value</span><span class="sxs-lookup"><span data-stu-id="f5e9c-112">Value</span></span>  |<span data-ttu-id="f5e9c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f5e9c-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f5e9c-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f5e9c-114">0x8004101d</span></span> | <span data-ttu-id="f5e9c-115">Došlo k vnitřní chybě.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f5e9c-116">0</span><span class="sxs-lookup"><span data-stu-id="f5e9c-116">0</span></span> | <span data-ttu-id="f5e9c-117">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f5e9c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5e9c-118">Remarks</span></span>

<span data-ttu-id="f5e9c-119">Tato funkce zalamuje volání na [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) metody.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="f5e9c-120">Volající začne, pomocí pořadí výčtu [funkce BeginMethodEnumeration](beginmethodenumeration.md)a pak zavolá [NextMethod funkce](nextmethod.md )dokud metoda vrátí `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="f5e9c-121">Volající volitelně dokončením sekvence pomocí volání `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="f5e9c-122">Volající může již v rané fázi ukončit výčtu voláním `EndMethodEnumeration` kdykoli.</span><span class="sxs-lookup"><span data-stu-id="f5e9c-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5e9c-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5e9c-123">Requirements</span></span>  
 <span data-ttu-id="f5e9c-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5e9c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5e9c-125">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f5e9c-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f5e9c-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f5e9c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e9c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5e9c-127">See also</span></span>

- [<span data-ttu-id="f5e9c-128">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f5e9c-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
