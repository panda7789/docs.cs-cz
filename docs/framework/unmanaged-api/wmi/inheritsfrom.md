---
title: InheritsFrom funkce (Nespravované rozhraní API Reference)
description: Funkce InheritsFrom určuje, zda je třída nebo instance odvozena z určité nadřazené třídy.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174937"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="f57d0-103">InheritsFrom,</span><span class="sxs-lookup"><span data-stu-id="f57d0-103">InheritsFrom function</span></span>
<span data-ttu-id="f57d0-104">Určuje, zda aktuální třída nebo instance pochází z zadané nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="f57d0-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f57d0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57d0-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="f57d0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f57d0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f57d0-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="f57d0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f57d0-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="f57d0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="f57d0-109">[v] Název třídy.</span><span class="sxs-lookup"><span data-stu-id="f57d0-109">[in] The name of the class.</span></span> <span data-ttu-id="f57d0-110">`wszAncestor`musí ukazovat na `LPCWSTR`platný .</span><span class="sxs-lookup"><span data-stu-id="f57d0-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f57d0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f57d0-111">Return value</span></span>

<span data-ttu-id="f57d0-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f57d0-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f57d0-113">Trvalé</span><span class="sxs-lookup"><span data-stu-id="f57d0-113">Constant</span></span>  |<span data-ttu-id="f57d0-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f57d0-114">Value</span></span>  |<span data-ttu-id="f57d0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f57d0-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f57d0-116">0</span><span class="sxs-lookup"><span data-stu-id="f57d0-116">0</span></span> | <span data-ttu-id="f57d0-117">Aktuální objekt dědí `wszAncestor`z .</span><span class="sxs-lookup"><span data-stu-id="f57d0-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="f57d0-118">1</span><span class="sxs-lookup"><span data-stu-id="f57d0-118">1</span></span> | <span data-ttu-id="f57d0-119">Aktuální objekt nedědí `wszAncestor`z .</span><span class="sxs-lookup"><span data-stu-id="f57d0-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f57d0-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f57d0-120">0x80041008</span></span> | <span data-ttu-id="f57d0-121">`wszAncestor` je `null`.</span><span class="sxs-lookup"><span data-stu-id="f57d0-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="f57d0-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f57d0-122">Remarks</span></span>

<span data-ttu-id="f57d0-123">Tato funkce zabalí volání [metody IWbemClassObject::InheritsFrom.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)</span><span class="sxs-lookup"><span data-stu-id="f57d0-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f57d0-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f57d0-124">Requirements</span></span>  
 <span data-ttu-id="f57d0-125">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f57d0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57d0-126">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f57d0-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f57d0-127">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f57d0-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57d0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f57d0-128">See also</span></span>

- [<span data-ttu-id="f57d0-129">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f57d0-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
