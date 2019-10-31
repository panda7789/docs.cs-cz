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
ms.openlocfilehash: 6bda63377251e3a208dfb1620896535ccdf8ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127433"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="19d5c-103">InheritsFrom – funkce</span><span class="sxs-lookup"><span data-stu-id="19d5c-103">InheritsFrom function</span></span>
<span data-ttu-id="19d5c-104">Určuje, zda aktuální třída nebo instance je odvozena ze zadané nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="19d5c-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="19d5c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19d5c-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="19d5c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="19d5c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="19d5c-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="19d5c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="19d5c-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="19d5c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="19d5c-109">pro Název třídy.</span><span class="sxs-lookup"><span data-stu-id="19d5c-109">[in] The name of the class.</span></span> <span data-ttu-id="19d5c-110">`wszAncestor` musí ukazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="19d5c-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="19d5c-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="19d5c-111">Return value</span></span>

<span data-ttu-id="19d5c-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="19d5c-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="19d5c-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="19d5c-113">Constant</span></span>  |<span data-ttu-id="19d5c-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="19d5c-114">Value</span></span>  |<span data-ttu-id="19d5c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="19d5c-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="19d5c-116">0,8</span><span class="sxs-lookup"><span data-stu-id="19d5c-116">0</span></span> | <span data-ttu-id="19d5c-117">Aktuální objekt dědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="19d5c-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="19d5c-118">první</span><span class="sxs-lookup"><span data-stu-id="19d5c-118">1</span></span> | <span data-ttu-id="19d5c-119">Aktuální objekt nedědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="19d5c-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="19d5c-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="19d5c-120">0x80041008</span></span> | <span data-ttu-id="19d5c-121">`wszAncestor` je `null`.</span><span class="sxs-lookup"><span data-stu-id="19d5c-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="19d5c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19d5c-122">Remarks</span></span>

<span data-ttu-id="19d5c-123">Tato funkce zalomí volání metody [IWbemclassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .</span><span class="sxs-lookup"><span data-stu-id="19d5c-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="19d5c-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19d5c-124">Requirements</span></span>  
 <span data-ttu-id="19d5c-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d5c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d5c-126">**Hlavička:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="19d5c-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="19d5c-127">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19d5c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d5c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19d5c-128">See also</span></span>

- [<span data-ttu-id="19d5c-129">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="19d5c-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
