---
title: Clone – funkce (odkaz na nespravované rozhraní API)
description: Funkce Clone vrátí nový objekt, který je úplným klonem aktuálního.
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
ms.openlocfilehash: 5957f591dca7df30178660eb3fb074567c285715
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798710"
---
# <a name="clone-function"></a><span data-ttu-id="f650f-103">Funkce Clone</span><span class="sxs-lookup"><span data-stu-id="f650f-103">Clone function</span></span>
<span data-ttu-id="f650f-104">Vrátí nový objekt, který je úplným klonem aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="f650f-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f650f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f650f-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="f650f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f650f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f650f-107">pro Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="f650f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f650f-108">pro Ukazatel na instanci [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="f650f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="f650f-109">mimo Nový objekt, který je úplným jedinoum `ptr`.</span><span class="sxs-lookup"><span data-stu-id="f650f-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="f650f-110">Tento argument nemůže být `null` , pokud obdrží kopii aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="f650f-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="f650f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f650f-111">Return value</span></span>

<span data-ttu-id="f650f-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="f650f-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f650f-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="f650f-113">Constant</span></span>  |<span data-ttu-id="f650f-114">Value</span><span class="sxs-lookup"><span data-stu-id="f650f-114">Value</span></span>  |<span data-ttu-id="f650f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f650f-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f650f-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f650f-116">0x80041001</span></span> | <span data-ttu-id="f650f-117">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="f650f-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f650f-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f650f-118">0x80041008</span></span> | <span data-ttu-id="f650f-119">`null`byl zadán jako parametr a není platný v tomto použití.</span><span class="sxs-lookup"><span data-stu-id="f650f-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f650f-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f650f-120">0x80041006</span></span> | <span data-ttu-id="f650f-121">K naklonování objektu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="f650f-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f650f-122">0</span><span class="sxs-lookup"><span data-stu-id="f650f-122">0</span></span> | <span data-ttu-id="f650f-123">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f650f-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f650f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f650f-124">Remarks</span></span>

<span data-ttu-id="f650f-125">Tato funkce zalomí volání metody [IWbemclassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="f650f-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="f650f-126">Klonovaný objekt je objekt modelu COM, který má počet odkazů 1.</span><span class="sxs-lookup"><span data-stu-id="f650f-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="f650f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f650f-127">Requirements</span></span>  
 <span data-ttu-id="f650f-128">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f650f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f650f-129">**Hlaviček** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f650f-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f650f-130">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f650f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f650f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f650f-131">See also</span></span>

- [<span data-ttu-id="f650f-132">WMI a čítače výkonu (Reference nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="f650f-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
