---
title: InheritsFrom – funkce (Reference nespravovaného rozhraní API)
description: Funkce InheritsFrom určuje, zda je třída nebo instance odvozena z konkrétní nadřazené třídy.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c32c54ec56ea0fe4f4039ca6438a91338edbadb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798447"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="74146-103">InheritsFrom – funkce</span><span class="sxs-lookup"><span data-stu-id="74146-103">InheritsFrom function</span></span>
<span data-ttu-id="74146-104">Určuje, zda aktuální třída nebo instance je odvozena ze zadané nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="74146-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="74146-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74146-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="74146-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74146-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="74146-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="74146-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="74146-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="74146-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="74146-109">pro Název třídy.</span><span class="sxs-lookup"><span data-stu-id="74146-109">[in] The name of the class.</span></span> <span data-ttu-id="74146-110">`wszAncestor`musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="74146-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="74146-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74146-111">Return value</span></span>

<span data-ttu-id="74146-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="74146-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="74146-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="74146-113">Constant</span></span>  |<span data-ttu-id="74146-114">Value</span><span class="sxs-lookup"><span data-stu-id="74146-114">Value</span></span>  |<span data-ttu-id="74146-115">Popis</span><span class="sxs-lookup"><span data-stu-id="74146-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="74146-116">0</span><span class="sxs-lookup"><span data-stu-id="74146-116">0</span></span> | <span data-ttu-id="74146-117">Aktuální objekt dědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="74146-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="74146-118">1</span><span class="sxs-lookup"><span data-stu-id="74146-118">1</span></span> | <span data-ttu-id="74146-119">Aktuální objekt nedědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="74146-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="74146-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="74146-120">0x80041008</span></span> | <span data-ttu-id="74146-121">`wszAncestor`je `null`.</span><span class="sxs-lookup"><span data-stu-id="74146-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="74146-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74146-122">Remarks</span></span>

<span data-ttu-id="74146-123">Tato funkce zalomí volání metody [IWbemclassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .</span><span class="sxs-lookup"><span data-stu-id="74146-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74146-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74146-124">Requirements</span></span>  
 <span data-ttu-id="74146-125">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74146-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74146-126">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="74146-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="74146-127">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74146-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74146-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74146-128">See also</span></span>

- [<span data-ttu-id="74146-129">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="74146-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
