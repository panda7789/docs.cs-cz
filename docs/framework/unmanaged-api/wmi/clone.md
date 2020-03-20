---
title: Clone function (Unmanaged API Reference)
description: Funkce Clone vrátí nový objekt, který je úplným klonem aktuálního objektu.
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
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176848"
---
# <a name="clone-function"></a><span data-ttu-id="75e7e-103">Funkce Clone</span><span class="sxs-lookup"><span data-stu-id="75e7e-103">Clone function</span></span>
<span data-ttu-id="75e7e-104">Vrátí nový objekt, který je úplným klonem aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="75e7e-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75e7e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75e7e-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="75e7e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75e7e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75e7e-107">[v] Tento parametr není použit.</span><span class="sxs-lookup"><span data-stu-id="75e7e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="75e7e-108">[v] Ukazatel na instanci [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="75e7e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="75e7e-109">[out] Nový objekt, který je `ptr`úplnou osamělost .</span><span class="sxs-lookup"><span data-stu-id="75e7e-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="75e7e-110">Tento argument `null` nemůže být, pokud obdrží kopii aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="75e7e-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="75e7e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75e7e-111">Return value</span></span>

<span data-ttu-id="75e7e-112">Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:</span><span class="sxs-lookup"><span data-stu-id="75e7e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75e7e-113">Trvalé</span><span class="sxs-lookup"><span data-stu-id="75e7e-113">Constant</span></span>  |<span data-ttu-id="75e7e-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="75e7e-114">Value</span></span>  |<span data-ttu-id="75e7e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="75e7e-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="75e7e-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="75e7e-116">0x80041001</span></span> | <span data-ttu-id="75e7e-117">Došlo k obecnému selhání.</span><span class="sxs-lookup"><span data-stu-id="75e7e-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75e7e-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75e7e-118">0x80041008</span></span> | <span data-ttu-id="75e7e-119">`null`byl zadán jako parametr a není v tomto použití legální.</span><span class="sxs-lookup"><span data-stu-id="75e7e-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="75e7e-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="75e7e-120">0x80041006</span></span> | <span data-ttu-id="75e7e-121">K klonování objektu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="75e7e-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="75e7e-122">0</span><span class="sxs-lookup"><span data-stu-id="75e7e-122">0</span></span> | <span data-ttu-id="75e7e-123">Volání funkce bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="75e7e-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75e7e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75e7e-124">Remarks</span></span>

<span data-ttu-id="75e7e-125">Tato funkce zabalí volání [metody IWbemClassObject::Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="75e7e-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="75e7e-126">Klonovaný objekt je objekt COM, který má počet odkazů 1.</span><span class="sxs-lookup"><span data-stu-id="75e7e-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="75e7e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75e7e-127">Requirements</span></span>  
 <span data-ttu-id="75e7e-128">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75e7e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e7e-129">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75e7e-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75e7e-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75e7e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e7e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="75e7e-131">See also</span></span>

- [<span data-ttu-id="75e7e-132">Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="75e7e-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
