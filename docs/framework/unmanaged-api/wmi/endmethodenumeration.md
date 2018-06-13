---
title: Funkce EndMethodEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce EndMethodEnumeration ukončí sekvenci metoda výčtu.
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
ms.openlocfilehash: d09a2ee278dba7e711891bc6d72043bb3a499dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458487"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="cd6a2-103">EndMethodEnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="cd6a2-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="cd6a2-104">Ukončí v sekvenci výčtu začít s volání [BeginMethodEnumeration funkce](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a2-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="cd6a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd6a2-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="cd6a2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd6a2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cd6a2-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cd6a2-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd6a2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd6a2-109">Return value</span></span>

<span data-ttu-id="cd6a2-110">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="cd6a2-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cd6a2-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="cd6a2-111">Constant</span></span>  |<span data-ttu-id="cd6a2-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cd6a2-112">Value</span></span>  |<span data-ttu-id="cd6a2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cd6a2-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="cd6a2-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="cd6a2-114">0x8004101d</span></span> | <span data-ttu-id="cd6a2-115">Došlo k vnitřní chybě.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cd6a2-116">0</span><span class="sxs-lookup"><span data-stu-id="cd6a2-116">0</span></span> | <span data-ttu-id="cd6a2-117">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="cd6a2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd6a2-118">Remarks</span></span>

<span data-ttu-id="cd6a2-119">Tato funkce zabalí volání [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="cd6a2-120">Volající začne, pomocí pořadí výčtu [BeginMethodEnumeration funkce](beginmethodenumeration.md)a potom zavolá [NextMethod funkce](nextmethod.md )dokud vrátí metoda `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="cd6a2-121">Volající volitelně dokončení sekvenci voláním `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="cd6a2-122">Volající ukončovat výčtu již v rané fázi voláním `EndMethodEnumeration` kdykoli.</span><span class="sxs-lookup"><span data-stu-id="cd6a2-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd6a2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd6a2-123">Requirements</span></span>  
 <span data-ttu-id="cd6a2-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6a2-125">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cd6a2-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cd6a2-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6a2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6a2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd6a2-127">See also</span></span>  
[<span data-ttu-id="cd6a2-128">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="cd6a2-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
