---
title: BeginMethodEnumeration – funkce (Reference nespravovaného rozhraní API)
description: Funkce BeginMethodEnumeration zahájí výčet metod objektu.
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
ms.openlocfilehash: be1e86e0b760ab403cf42ac19da03f84769a85cf
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884420"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="566bf-103">Funkce BeginMethodEnumeration</span><span class="sxs-lookup"><span data-stu-id="566bf-103">BeginMethodEnumeration function</span></span>
<span data-ttu-id="566bf-104">Spustí výčet metod, které jsou k dispozici pro objekt.</span><span class="sxs-lookup"><span data-stu-id="566bf-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="566bf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="566bf-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="566bf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="566bf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="566bf-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="566bf-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="566bf-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="566bf-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="566bf-109">pro Nula (0) pro všechny metody nebo příznak, který určuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="566bf-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="566bf-110">Následující příznaky jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="566bf-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="566bf-111">Konstanta</span><span class="sxs-lookup"><span data-stu-id="566bf-111">Constant</span></span>  |<span data-ttu-id="566bf-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="566bf-112">Value</span></span>  |<span data-ttu-id="566bf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="566bf-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="566bf-114">0x10</span><span class="sxs-lookup"><span data-stu-id="566bf-114">0x10</span></span> | <span data-ttu-id="566bf-115">Omezte výčet na metody, které jsou definovány ve třídě samotné.</span><span class="sxs-lookup"><span data-stu-id="566bf-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="566bf-116">0x20</span><span class="sxs-lookup"><span data-stu-id="566bf-116">0x20</span></span> | <span data-ttu-id="566bf-117">Omezte výčet na vlastnosti, které jsou zděděné ze základních tříd.</span><span class="sxs-lookup"><span data-stu-id="566bf-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="566bf-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="566bf-118">Return value</span></span>

<span data-ttu-id="566bf-119">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="566bf-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="566bf-120">Konstanta</span><span class="sxs-lookup"><span data-stu-id="566bf-120">Constant</span></span>  |<span data-ttu-id="566bf-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="566bf-121">Value</span></span>  |<span data-ttu-id="566bf-122">Popis</span><span class="sxs-lookup"><span data-stu-id="566bf-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="566bf-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="566bf-123">0x80041008</span></span> | <span data-ttu-id="566bf-124">`lEnnumFlags` je nenulová a není jedním z určených příznaků.</span><span class="sxs-lookup"><span data-stu-id="566bf-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="566bf-125">0</span><span class="sxs-lookup"><span data-stu-id="566bf-125">0</span></span> | <span data-ttu-id="566bf-126">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="566bf-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="566bf-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="566bf-127">Remarks</span></span>

<span data-ttu-id="566bf-128">Tato funkce zalomí volání metody [IWbemclassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="566bf-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="566bf-129">Toto volání metody je podporováno pouze v případě, že aktuální objekt je definice třídy.</span><span class="sxs-lookup"><span data-stu-id="566bf-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="566bf-130">Manipulace s metodou není k dispozici z ukazatelů [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , které odkazují na instance.</span><span class="sxs-lookup"><span data-stu-id="566bf-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="566bf-131">Pořadí, ve kterém jsou metody výčty, je zaručené pro danou instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)jako invariantní.</span><span class="sxs-lookup"><span data-stu-id="566bf-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="566bf-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="566bf-132">Requirements</span></span>  
 <span data-ttu-id="566bf-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="566bf-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="566bf-134">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="566bf-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="566bf-135">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="566bf-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566bf-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="566bf-136">See also</span></span>

- [<span data-ttu-id="566bf-137">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="566bf-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
