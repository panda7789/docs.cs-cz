---
title: Klonovat – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Klonování funkce vrátí nový objekt, který je kompletní klonu stávající.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b027d26292b5d810d91932bac4ec8dee4b77661d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643283"
---
# <a name="clone-function"></a><span data-ttu-id="67c96-103">Funkce clone</span><span class="sxs-lookup"><span data-stu-id="67c96-103">Clone function</span></span>
<span data-ttu-id="67c96-104">Vrátí nový objekt, který je kompletní klon aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="67c96-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="67c96-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67c96-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="67c96-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="67c96-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="67c96-107">[in] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="67c96-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="67c96-108">[in] Ukazatel [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="67c96-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="67c96-109">[out] Nový objekt, který je kompletní jedinou z `ptr`.</span><span class="sxs-lookup"><span data-stu-id="67c96-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="67c96-110">Tento argument nemůže být `null` pokud obdrží kopii aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="67c96-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="67c96-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="67c96-111">Return value</span></span>

<span data-ttu-id="67c96-112">Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="67c96-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="67c96-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="67c96-113">Constant</span></span>  |<span data-ttu-id="67c96-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67c96-114">Value</span></span>  |<span data-ttu-id="67c96-115">Popis</span><span class="sxs-lookup"><span data-stu-id="67c96-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="67c96-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="67c96-116">0x80041001</span></span> | <span data-ttu-id="67c96-117">Obecné selhání došlo.</span><span class="sxs-lookup"><span data-stu-id="67c96-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="67c96-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="67c96-118">0x80041008</span></span> | <span data-ttu-id="67c96-119">`null` byl zadán jako parametr, a není povoleno v použití těchto.</span><span class="sxs-lookup"><span data-stu-id="67c96-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="67c96-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="67c96-120">0x80041006</span></span> | <span data-ttu-id="67c96-121">Nedostatek paměti je k dispozici ke klonování objektu.</span><span class="sxs-lookup"><span data-stu-id="67c96-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="67c96-122">0</span><span class="sxs-lookup"><span data-stu-id="67c96-122">0</span></span> | <span data-ttu-id="67c96-123">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="67c96-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="67c96-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67c96-124">Remarks</span></span>

<span data-ttu-id="67c96-125">Tato funkce zalamuje volání na [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) metody.</span><span class="sxs-lookup"><span data-stu-id="67c96-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="67c96-126">Klonovaný objekt je objekt modelu COM, který obsahuje počet odkazů hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="67c96-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="67c96-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67c96-127">Requirements</span></span>  
 <span data-ttu-id="67c96-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67c96-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67c96-129">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="67c96-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="67c96-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67c96-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c96-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67c96-131">See also</span></span>
- [<span data-ttu-id="67c96-132">WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="67c96-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
