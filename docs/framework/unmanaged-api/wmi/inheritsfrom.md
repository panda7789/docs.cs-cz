---
title: Funkce InheritsFrom (referenční dokumentace nespravovaného rozhraní API)
description: Funkce InheritsFrom Určuje, zda třídy nebo instance je odvozena z určité nadřazené třídy.
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
ms.openlocfilehash: 4784e22d5a3eec031fbee00441958a62d66b52df
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542651"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="6ec6f-103">InheritsFrom – funkce</span><span class="sxs-lookup"><span data-stu-id="6ec6f-103">InheritsFrom function</span></span>
<span data-ttu-id="6ec6f-104">Určuje, zda aktuální třídy nebo instance je odvozena od třídy zadaný nadřazený prvek.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6ec6f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ec6f-105">Syntax</span></span>  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="6ec6f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ec6f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6ec6f-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6ec6f-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="6ec6f-109">[in] Název třídy.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-109">[in] The name of the class.</span></span> <span data-ttu-id="6ec6f-110">`wszAncestor` musí odkazovat na platný `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ec6f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ec6f-111">Return value</span></span>

<span data-ttu-id="6ec6f-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="6ec6f-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6ec6f-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="6ec6f-113">Constant</span></span>  |<span data-ttu-id="6ec6f-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ec6f-114">Value</span></span>  |<span data-ttu-id="6ec6f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6ec6f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6ec6f-116">0</span><span class="sxs-lookup"><span data-stu-id="6ec6f-116">0</span></span> | <span data-ttu-id="6ec6f-117">Aktuální objekt dědí z `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="6ec6f-118">1</span><span class="sxs-lookup"><span data-stu-id="6ec6f-118">1</span></span> | <span data-ttu-id="6ec6f-119">Aktuální objekt nedědí ze `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6ec6f-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6ec6f-120">0x80041008</span></span> | <span data-ttu-id="6ec6f-121">`wszAncestor` je `null`.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="6ec6f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ec6f-122">Remarks</span></span>

<span data-ttu-id="6ec6f-123">Tato funkce zalamuje volání na [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) metody.</span><span class="sxs-lookup"><span data-stu-id="6ec6f-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ec6f-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ec6f-124">Requirements</span></span>  
 <span data-ttu-id="6ec6f-125">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec6f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec6f-126">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6ec6f-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6ec6f-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec6f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec6f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ec6f-128">See also</span></span>  
[<span data-ttu-id="6ec6f-129">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="6ec6f-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
