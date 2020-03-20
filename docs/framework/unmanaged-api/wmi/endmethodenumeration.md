---
title: Funkce EndMethodEnumeration (Nespravovaný odkaz rozhraní API)
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
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175002"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="0889c-103">Funkce EndMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="0889c-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="0889c-104">Ukončí posloupnost výčtu spuštěnou voláním [funkce BeginMethodEnumeration .](beginmethodenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="0889c-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0889c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0889c-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="0889c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0889c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0889c-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="0889c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0889c-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="0889c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="0889c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0889c-109">Return value</span></span>

<span data-ttu-id="0889c-110">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="0889c-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0889c-111">Trvalé</span><span class="sxs-lookup"><span data-stu-id="0889c-111">Constant</span></span>  |<span data-ttu-id="0889c-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0889c-112">Value</span></span>  |<span data-ttu-id="0889c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0889c-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="0889c-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="0889c-114">0x8004101d</span></span> | <span data-ttu-id="0889c-115">Došlo k vnitřní chybě.</span><span class="sxs-lookup"><span data-stu-id="0889c-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0889c-116">0</span><span class="sxs-lookup"><span data-stu-id="0889c-116">0</span></span> | <span data-ttu-id="0889c-117">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="0889c-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0889c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0889c-118">Remarks</span></span>

<span data-ttu-id="0889c-119">Tato funkce zabalí volání metody [IWbemClassObject::EndMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)</span><span class="sxs-lookup"><span data-stu-id="0889c-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="0889c-120">Volající zahájí posloupnost výčtu pomocí [funkce BeginMethodEnumeration a](beginmethodenumeration.md)potom zavolá `WBEM_S_NO_MORE_DATA`funkci [NextMethod,](nextmethod.md )dokud metoda nevrátí .</span><span class="sxs-lookup"><span data-stu-id="0889c-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="0889c-121">Volající volitelně dokončí pořadí voláním `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="0889c-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="0889c-122">Volající může ukončit výčtu `EndMethodEnumeration` brzy voláním kdykoli.</span><span class="sxs-lookup"><span data-stu-id="0889c-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="0889c-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0889c-123">Requirements</span></span>  
 <span data-ttu-id="0889c-124">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0889c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0889c-125">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0889c-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0889c-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0889c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0889c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0889c-127">See also</span></span>

- [<span data-ttu-id="0889c-128">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="0889c-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
