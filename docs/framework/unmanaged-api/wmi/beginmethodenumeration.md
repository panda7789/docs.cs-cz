---
title: Funkce BeginMethodEnumeration (Unmanaged API Reference)
description: Funkce BeginMethodEnumeration spustí výčet metod objektu.
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175041"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="13843-103">Funkce BeginMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="13843-103">BeginMethodEnumeration function</span></span>
<span data-ttu-id="13843-104">Začíná výčet metod, které jsou k dispozici pro objekt.</span><span class="sxs-lookup"><span data-stu-id="13843-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="13843-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13843-105">Syntax</span></span>  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="13843-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13843-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="13843-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="13843-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="13843-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="13843-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="13843-109">[v] Zero (0) pro všechny metody nebo příznak, který určuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="13843-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="13843-110">Následující příznaky jsou definovány v souboru hlavičky *WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="13843-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="13843-111">Trvalé</span><span class="sxs-lookup"><span data-stu-id="13843-111">Constant</span></span>  |<span data-ttu-id="13843-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="13843-112">Value</span></span>  |<span data-ttu-id="13843-113">Popis</span><span class="sxs-lookup"><span data-stu-id="13843-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="13843-114">0x10</span><span class="sxs-lookup"><span data-stu-id="13843-114">0x10</span></span> | <span data-ttu-id="13843-115">Omezte výčet na metody, které jsou definovány v samotné třídě.</span><span class="sxs-lookup"><span data-stu-id="13843-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="13843-116">0x20</span><span class="sxs-lookup"><span data-stu-id="13843-116">0x20</span></span> | <span data-ttu-id="13843-117">Omezte výčet na vlastnosti, které jsou zděděny ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="13843-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="13843-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13843-118">Return value</span></span>

<span data-ttu-id="13843-119">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="13843-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="13843-120">Trvalé</span><span class="sxs-lookup"><span data-stu-id="13843-120">Constant</span></span>  |<span data-ttu-id="13843-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="13843-121">Value</span></span>  |<span data-ttu-id="13843-122">Popis</span><span class="sxs-lookup"><span data-stu-id="13843-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="13843-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="13843-123">0x80041008</span></span> | <span data-ttu-id="13843-124">`lEnnumFlags`je nenulová a není jedním ze zadaných příznaků.</span><span class="sxs-lookup"><span data-stu-id="13843-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="13843-125">0</span><span class="sxs-lookup"><span data-stu-id="13843-125">0</span></span> | <span data-ttu-id="13843-126">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="13843-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="13843-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13843-127">Remarks</span></span>

<span data-ttu-id="13843-128">Tato funkce zabalí volání metody [IWbemClassObject::BeginMethodEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)</span><span class="sxs-lookup"><span data-stu-id="13843-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="13843-129">Toto volání metody je podporováno pouze v případě, že aktuální objekt je definice třídy.</span><span class="sxs-lookup"><span data-stu-id="13843-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="13843-130">Manipulace s metodami není k dispozici z ukazatelů [IWbemClassObject,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) které odkazují na instance.</span><span class="sxs-lookup"><span data-stu-id="13843-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="13843-131">Pořadí, ve kterém jsou metody výčtu je zaručeno, že je invariantpro danou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="13843-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="13843-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13843-132">Requirements</span></span>  
 <span data-ttu-id="13843-133">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13843-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13843-134">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="13843-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="13843-135">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13843-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13843-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="13843-136">See also</span></span>

- [<span data-ttu-id="13843-137">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="13843-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
