---
title: Clone – funkce (referenční dokumentace nespravovaného rozhraní API)
description: Funkce klonování vrací nový objekt, který je kompletní klonu stávající.
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
ms.openlocfilehash: c5841c89cf394502f68381dfed42593c9debdcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457313"
---
# <a name="clone-function"></a><span data-ttu-id="37367-103">Clone – funkce</span><span class="sxs-lookup"><span data-stu-id="37367-103">Clone function</span></span>
<span data-ttu-id="37367-104">Vrátí nový objekt, který je kompletní klonem aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="37367-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="37367-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37367-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="37367-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37367-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="37367-107">[v] Tento parametr se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="37367-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="37367-108">[v] Ukazatel na [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="37367-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppCopy`  
<span data-ttu-id="37367-109">[out] Nový objekt, který je úplná jedinou z `ptr`.</span><span class="sxs-lookup"><span data-stu-id="37367-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="37367-110">Tento argument nesmí být `null` pokud obdrží kopii aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="37367-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="37367-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37367-111">Return value</span></span>

<span data-ttu-id="37367-112">Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:</span><span class="sxs-lookup"><span data-stu-id="37367-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="37367-113">Konstanta</span><span class="sxs-lookup"><span data-stu-id="37367-113">Constant</span></span>  |<span data-ttu-id="37367-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37367-114">Value</span></span>  |<span data-ttu-id="37367-115">Popis</span><span class="sxs-lookup"><span data-stu-id="37367-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="37367-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="37367-116">0x80041001</span></span> | <span data-ttu-id="37367-117">Došlo k obecné chybě.</span><span class="sxs-lookup"><span data-stu-id="37367-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="37367-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="37367-118">0x80041008</span></span> | <span data-ttu-id="37367-119">`null` byla zadána jako parametr, a není právní v toto použití.</span><span class="sxs-lookup"><span data-stu-id="37367-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="37367-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="37367-120">0x80041006</span></span> | <span data-ttu-id="37367-121">Nedostatek paměti je k dispozici pro klonování objektu.</span><span class="sxs-lookup"><span data-stu-id="37367-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="37367-122">0</span><span class="sxs-lookup"><span data-stu-id="37367-122">0</span></span> | <span data-ttu-id="37367-123">Volání funkce byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="37367-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="37367-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37367-124">Remarks</span></span>

<span data-ttu-id="37367-125">Tato funkce zabalí volání [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metoda.</span><span class="sxs-lookup"><span data-stu-id="37367-125">This function wraps a call to the [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="37367-126">Objekt klonovaného je objekt modelu COM, který obsahuje počet odkazů 1.</span><span class="sxs-lookup"><span data-stu-id="37367-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="37367-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37367-127">Requirements</span></span>  
 <span data-ttu-id="37367-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37367-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37367-129">**Záhlaví:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="37367-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="37367-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="37367-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37367-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="37367-131">See also</span></span>  
[<span data-ttu-id="37367-132">Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)</span><span class="sxs-lookup"><span data-stu-id="37367-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
